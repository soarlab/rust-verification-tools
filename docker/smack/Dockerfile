FROM rvt_seahorn:latest

USER root

RUN apt-get update && \
      apt-get -y install \
      software-properties-common \
      wget \
      sudo \
      g++

RUN mkdir /home/smack
WORKDIR /home/smack

# ARG SMACK_VERSION

ENV INSTALL_Z3=0
ENV TEST_SMACK=0

RUN git clone --no-checkout https://github.com/smackers/smack.git smack \
  && cd smack \
  && git checkout rvt-test

RUN cd smack && bin/build.sh --prefix /home/smack/smack-install



# Borrowed from JFS
# Create `user` user for container with password `user`.  and give it
# password-less sudo access
# RUN useradd -m user && \
#     echo user:user | chpasswd && \
#     cp /etc/sudoers /etc/sudoers.bak && \
#     echo 'user  ALL=(root) NOPASSWD: ALL' >> /etc/sudoers

# USER user

# # Add the current directory to `/home/user/smack`
# ADD --chown=user . $SMACKDIR

# # Set the work directory
# WORKDIR $SMACKDIR

# # Build SMACK
# RUN bin/build.sh

# # Add envinronment
# RUN echo "source /home/user/smack.environment" >> ~/.bashrc
