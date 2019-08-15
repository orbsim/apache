FROM orbsim/debian:jessie
# --------- apache configuration
ENV APACHE_DOCUMENT_ROOT /var/www
ENV APACHE_RUN_USER  www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR   /var/log/apache2/
ENV APACHE_PID_FILE  /var/run/apache2/apache2.pid
ENV APACHE_RUN_DIR   /var/run/apache2
ENV APACHE_LOCK_DIR  /var/lock/apache2
# --------- preconfigure apache
RUN mkdir -p $APACHE_LOG_DIR
# --------- installing apache2
RUN echo "Installing Apache & Php" \
  && apt-get update -y \
  && apt-get install -y apache2 \
                        php5 \
                        php5-common \
                        php5-curl \
                        php5-dev \
                        php5-gd \
                        php5-interbase \
                        php5-ldap \
                        php5-mcrypt \
                        php5-mysql \
                        php-pear \
                        php5-pgsql \
                        php-tcpdf \
                        php5-xsl

RUN a2enmod rewrite ssl ldap
RUN chown -R ${APACHE_RUN_USER}:${APACHE_RUN_GROUP} ${APACHE_DOCUMENT_ROOT}
#-------------------------------------------------------------------
WORKDIR ${APACHE_DOCUMENT_ROOT}
EXPOSE 80 443
CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
