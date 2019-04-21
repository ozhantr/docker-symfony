FROM phpdockerio/php72-fpm:latest
# WORKDIR "/app"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install php7.2-mysql php-xdebug \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
    && apt-get -y install git \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN git config --global user.name "Ozhan Duran" \
    && git config --global user.email "ozhantr@hotmail.com"

# Install vim, nano, wget, tree, iputils-ping
RUN apt-get update \
    && apt-get -y install vim nano wget tree iputils-ping \
    && echo "alias @tree='tree -L 1'" >> ~/.bashrc \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN apt-get update \
    && composer global require friendsofphp/php-cs-fixer \
    && echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
    && echo "alias @symfony='php-cs-fixer fix \$PWD --rules=@Symfony'" >> ~/.bashrc \
    && echo "alias @psr2='php-cs-fixer fix \$PWD --rules=@PSR2'" >> ~/.bashrc
