FROM        ubuntu:14.04
MAINTAINER  V. Mogilevksy "https://github.com/viatcheslavmogilevsky"

# Ignore APT warnings about not having a TTY
ENV DEBIAN_FRONTEND noninteractive

# Ensure UTF-8 locale
RUN echo "LANG=\"en_US.UTF-8\"" > /etc/default/locale
RUN locale-gen en_US.UTF-8
RUN dpkg-reconfigure locales

# Install build dependencies
RUN apt-get update
RUN apt-get install -y software-properties-common
RUN apt-add-repository ppa:git-core/ppa
RUN apt-get update

RUN apt-get install -y \
  autoconf \
  bison \
  build-essential \
  curl \
  git \
  zlib1g-dev \
  libssl-dev \
  libreadline-dev \
  libncurses5-dev
RUN apt-get clean

# Install rbenv
RUN git clone https://github.com/sstephenson/rbenv.git /root/.rbenv
RUN echo '# rbenv setup' > /etc/profile.d/rbenv.sh
RUN echo 'export RBENV_ROOT=/root/.rbenv' >> /etc/profile.d/rbenv.sh
RUN echo 'export PATH="$RBENV_ROOT/bin:$PATH"' >> /etc/profile.d/rbenv.sh
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh
RUN chmod +x /etc/profile.d/rbenv.sh

# Install ruby-build
RUN mkdir /root/.rbenv/plugins
RUN git clone https://github.com/sstephenson/ruby-build.git /root/.rbenv/plugins/ruby-build

# Config gem
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc