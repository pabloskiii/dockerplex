# dockerplex
Aqui se subira el docker-compose utilizado en el despliegue de el contenedor de plex del proyecto integrado de ASIR de Pablo Villegas Aguilar

```

#Docker-Compose para el despliegue de un contenedor de plex media server
version: "3.4"                                  
services:
  plex:
    image: lscr.io/linuxserver/plex             #la imagen de plex que vamos a descargar e instalar
    container_name: plex
    network_mode: host
    ports:                                      #Definimos los puertos que se usaran para acceder al servicio y los asignaremos al contenedor
      - "32400:32400"
      - "1900:1900"
      - "3005:3005"
      - "5353:5353"
      - "8324:8324"
      - "32410:32410"
      - "32412:32412"
      - "32413:32413"
      - "32414:32414"
      - "32469:32469"
    environment:
      - PUID=1000
      - PGID=1000
      - VERSION=docker
      - PLEX_CLAIM=    #opcional, se puede obtener aqui https://www.plex.tv/claim/
    volumes:
      - plex_data:/config
      - /media/plexstorage:/media                 #montamos la carpeta remota donde esta nuestro contenido en el contenedor
    restart: always                               #Habilitamos que este contenedor se lance con el inicio del sistema
  
volumes:
  plex_data:
  
```
