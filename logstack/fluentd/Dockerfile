# logstack/fluentd/Dockerfile
FROM fluent/fluentd:v1.14-debian-1

USER root

# Install dependencies for Ruby 3.x
RUN apt-get update && apt-get install -y \
    build-essential \
    libssl-dev \
    zlib1g-dev \
    libreadline-dev \
    libyaml-dev \
    libsqlite3-dev \
    sqlite3 \
    libxml2-dev \
    libxslt1-dev \
    libcurl4-openssl-dev \
    software-properties-common \
    libffi-dev \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Install Ruby 3.0.0 from source
RUN cd /tmp && \
    wget http://ftp.ruby-lang.org/pub/ruby/3.0/ruby-3.0.0.tar.gz && \
    tar -xzvf ruby-3.0.0.tar.gz && \
    cd ruby-3.0.0/ && \
    ./configure && \
    make && \
    make install && \
    cd .. && \
    rm -rf ruby-3.0.0*

# Install the Elasticsearch plugin
RUN gem install fluent-plugin-elasticsearch --no-document

USER fluent
