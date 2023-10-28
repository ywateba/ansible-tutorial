FROM ubuntu:20.04

RUN apt update &&  \
    apt install -y software-properties-common && \
    apt install -y openssh-server && \
    apt install -y python3-pip python3-pip python3-setuptools && \
    pip install ansible


RUN mkdir /etc/ansible/ && mkdir /var/run/sshd

RUN echo -e '[local]\nlocalhost' > /etc/ansible/hosts
RUN echo 'root:redhat' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN addgroup  --group ansible && adduser --group  --system ansible 

WORKDIR /home/ansible

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]
USER ansible

