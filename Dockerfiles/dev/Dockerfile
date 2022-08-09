FROM python:3.6

# add our user and group first to make sure their IDs get assigned consistently, regardless of whatever dependencies get added
RUN groupadd -r pipelines && useradd -m -r -g pipelines pipelines

# Install pipelines
RUN /usr/local/bin/python -m pip install --upgrade pip
RUN pip install git+git://github.com/Wiredcraft/pipelines@master
RUN mkdir /workspace && chown pipelines:pipelines /workspace
VOLUME /workspace
WORKDIR /workspace

ENV ADMIN_USER admin
ENV ADMIN_PASS admin
ENV WORKSPACE /workspace

EXPOSE 8888

CMD pipelines server --workspace ${WORKSPACE} --username ${ADMIN_USER} --password ${ADMIN_PASS} --host 0.0.0.0
