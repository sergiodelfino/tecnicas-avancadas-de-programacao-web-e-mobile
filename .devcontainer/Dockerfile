FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    git \
    git-lfs \
    openjdk-21-jdk \
    maven \
    mysql-server \
    && rm -rf /var/lib/apt/lists/*

RUN echo "CREATE USER 'sergio'@'localhost' IDENTIFIED BY 'q1w2e3r4'; \
        GRANT ALL PRIVILEGES ON *.* TO 'sergio'@'localhost' WITH GRANT OPTION; \
        DELETE FROM mysql.user WHERE User=''; \
        FLUSH PRIVILEGES;" > /tmp/script.sql

RUN service mysql start && \
    sleep 5 && \
    mysql -uroot < /tmp/script.sql && \
    service mysql stop

WORKDIR /workspaces/tecnicas-avancadas-de-programacao-web-e-mobile

CMD [ "bash" ]