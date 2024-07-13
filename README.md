# Debugear una aplicacion en PHP con Docker en PhpStorm

Este repositorio es para que los desarrolladores que quieren poder debugear una aplicacion en PHP dentro de un contenedor de docker usando Visual Studio Code.

*PHP Framework: CodeIgniter*

*Nota: Esto aplica para cualquier framework, pero se debe de modificar el archivo [entrypoint.sh](https://github.com/whatdacode/php-docker-phpstorm/blob/main/entrypoint.sh)*

## Pasos para crear el entorno

1. Creacion del archivo [docker-compose.yml](https://github.com/whatdacode/php-docker-phpstorm/blob/main/docker-compose.yml)
2. Creacion del archivo [Dockerfile](https://github.com/whatdacode/php-docker-phpstorm/blob/main/Dockerfile)
3. Creacion del archivo [entrypoint.sh](https://github.com/whatdacode/php-docker-phpstorm/blob/main/entrypoint.sh)
4. Creacion del archivo [xdebug.ini](https://github.com/whatdacode/php-docker-phpstorm/blob/main/xdebug.ini)

## Pasos para poder debugearlo

1. Configurar el puerto de Xdebug
   1. Ir a <code>File > Settings> PHP > Debug</code>
   2. Modificar el puerto en la seccion Xdebug a 9003
2. Agregar un nuevo servidor
   1. Ir a <code>File > Settings> PHP > Servers</code>
   2. Agregar un nuevo servidor con las siguientes opciones:
      - Nombre: <code>Docker - Localhost</code>
      - Host: <code>localhost</code>
      - Puerto: 8080
      - Selecciona la opcion <code>Use path mappings</code>
      - Mapea la carpeta <code>src</code> del proyecto a <code>/var/www/html</code>
3. Configurar <code>PHP Remote Debug</code>
   - Ir a <code>Run > Edit configurations</code>
   - Has click en la opcion <code>+</code> y selecciona <code>PHP Remote Debug</code>
   - Coloca el nombre a la configuracion
   - Elige el servidor creado en el paso anterior
   - Ingresa <code>PHPSTORM</code> en el campo <code>IDE key</code>

## Pasos para debugear

1. Debes ejecutar docker-compose up -d --build o docker compose up -d --build si estas utilizando la version 2 de Docker Desktop
2. Haz clic en el boton <code>Start Listening for PHP Debug Connections</code> en PhpStorm
3. Selecciona la configuracion creada en el punto anterior y haz clic en <code>Debug</code>
4. Coloca los breakpoints en el codigo que deseas debugear