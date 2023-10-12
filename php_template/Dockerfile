# Usar imagen base de PHP 7.4 con Apache
FROM php:7.4-apache

# Actualizar índice de paquetes y descargar paquetes necesarios
RUN apt-get update && \
    apt-get install -y \
    libpq-dev \
    git \
    zip \
    unzip 
#   && apt-get install -y mysql-server mysql-client libmysqlclient-dev --no-install-recommends \
#   && docker-php-ext-install pdo pdo_mysql \
#   && apt-get clean \
#   && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Instalar extensiones PHP necesarias
# RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysql pdo pdo_mysql

# Habilitar el módulo Apache Rewrite
RUN a2enmod rewrite

# Copiar el archivo de configuración de Apache
# COPY ./myconf/apache-config.conf /etc/apache2/sites-available/000-default.conf

# Descargar e instalar Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Establecer el directorio de trabajo
WORKDIR /var/www/html

# Copiar el archivo de configuración de PHP
# COPY ./myconf/php.ini /usr/local/etc/php/

# Copiar el código fuente de la aplicación
# COPY ./src /var/www/html/phptemplate

# Establecer permisos de escritura para la carpeta de caché de Composer
RUN chown -R www-data:www-data /var/www/html
# RUN mkdir /var/www/html/storage
RUN chmod a+rwx /var/www/html/

# Exponer el puerto 80
EXPOSE 80