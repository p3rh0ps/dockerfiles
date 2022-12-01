FROM alpine:3.16.2

LABEL description="Toolbox with Linux Alpine 3.16.2 \
python(3.10.5) / pip3(22.0.4) \
ansible-core(2.13.5) \
ansible nxos(4.0.0)/aci(2.3.0) collections [playbooks/roles] \
Ready For Use from Day-0 to Day-X"
LABEL maintainer="p3rh0ps <p3rh0ps@gmail.com>"
LABEL version="0.45"

RUN apk add vim && \
apk add git && \
apk add jq && \
apk add gcc && \
apk add libc-dev && \
apk add libssh-dev && \
apk add python3-dev && \
apk add python3 && \
apk add py3-pip && \
/usr/bin/python3 -m venv vpy3

RUN source /vpy3/bin/activate && \
/vpy3/bin/python3 -m pip install --upgrade && \
pip3 install wheel && \
pip3 install ansible-core==2.13.5 && \
pip3 install ansible-pylibssh==1.0.0 && \
pip3 install jmespath==1.0.1 && \
pip3 install pyang==2.5.3 && \
ansible-galaxy collection install cisco.nxos:=4.0.0 && \
ansible-galaxy collection install cisco.aci:=2.3.0 && \
ansible-galaxy collection install ansible.posix:=1.4.0 && \
ansible-galaxy collection install ansible.netcommon:=4.0.0 && \
ansible-galaxy collection install ansible.utils:=2.6.1 && \
ansible-galaxy collection install community.general:=6.0.0

RUN mkdir /playbooks
COPY ./playbooks /playbooks

RUN alias v=vim

ENTRYPOINT ["/bin/sh"]
