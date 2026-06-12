---
title: "Problema con las actualizaciones"
date: 2009-06-01
forum: Hardware
---

### Post by FB91 on 2009-06-01
Hace bastante tiempo no podía hacer andar internet en Ubuntu (mediante WiFi), ahora ya pude lograrlo (pero por una red cableada) y el problema es el siguiente:

Internet me va bien, este mismo post lo estoy escribiendo desde Ubuntu. Pero el problema es que cuando busco actualizaciones y pongo para descargar algún paquete me tira error.

Por ejemplo, si escribo **sudo apt-get update** en la consola, el resultado es este:

> fb91@PCFabricio:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-es                 
  No pude conectarme a 192.168.1.2 6588:
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg                           
  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-es               
  No pude conectarme a 192.168.1.2 6588:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-es             
  No pude conectarme a 192.168.1.2 6588:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty Release.gpg
  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/main Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/restricted Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/universe Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/multiverse Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates Release.gpg
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/restricted Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/universe Translation-es
  No pude conectarme a 192.168.1.2 6588:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/multiverse Translation-es
  No pude conectarme a 192.168.1.2 6588:
Leyendo lista de paquetes... Hecho         
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión

W: Imposible obtener [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-es.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Imposible obtener [http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg](http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg)  No pude conectarme a 192.168.1.2:6588 (192.168.1.2), expiró tiempo para conexión

W: Imposible obtener [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-es.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-es.bz2)  No pude conectarme a 192.168.1.2 6588:

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas¿Consejos?
Gracias :D

---

### Post by guillermolisi on 2009-06-01
> **FB91 said:**
> Hace bastante tiempo no podía hacer andar internet en Ubuntu (mediante WiFi), ahora ya pude lograrlo (pero por una red cableada) y el problema es el siguiente:

Internet me va bien, este mismo post lo estoy escribiendo desde Ubuntu. Pero el problema es que cuando busco actualizaciones y pongo para descargar algún paquete me tira error.

Por ejemplo, si escribo **sudo apt-get update** en la consola, el resultado es este:

¿Consejos?
Gracias :D
Sabes a que maquina/dispositivo le corresponde la IP 192.168.1.2:6588 (este ultimo numero es el port de lo que pareceria tenes configurado como proxy para las conexiones a Internet).

Si esto lo haces en la maquina que posee la conexion a Internet y no tenes proxy alguno en elmedio, esos datos estan de mas y por eso no funciona la actualziacion.

Si queres verificar, abri Sistema / Preferencias / Proxy de la red y fijate si que tenes configurado como proxy.

---

### Post by cuevas on 2009-08-25
Tenia el mismo problema. Resulta que en las preferencias del proxy de la red se encontraba seleccionada la opción "Configuración automática del proxy". Lo que hice fue cambiarla a "Conexión directa a internet" y se solucionó el problema.

Gracias!!

---

