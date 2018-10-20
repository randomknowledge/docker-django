FROM python:3.6

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        apt-transport-https \
        postgresql-client \
        wget \
	bzip2 \
	locales \
	libpq-dev \
	libjpeg-dev \
	liblcms2-dev \
	libfreetype6 \
	libfontconfig \
	libpcre3 \
	libpcre3-dev \
	zlib1g-dev \
	libxml2-dev \
	libxslt1-dev \
	fontforge \
	ttfautohint \
	ruby-dev \
	rubygems \
	gettext \
    && apt-get autoremove -y \
	&& apt-get clean all \
	&& rm -rf /var/lib/apt/lists/*

RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
	&& locale-gen \
	&& update-locale LANG=en_US.UTF-8

ENV LANG=en_US.UTF-8

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash
RUN apt-get -y install nodejs yarn

RUN groupadd -r wsgi --gid=1000
RUN useradd -r -g wsgi --uid=1000 wsgi
RUN pip install --ignore-installed --upgrade setuptools wheel pip

RUN mkdir -p /web/media /web/static /web/src

CMD ["bash"]
