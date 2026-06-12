---
title: "Webcam genius GF112 no corre en Skype 2.1 (beta)"
date: 2009-11-22
forum: Hardware
---

### Post by Italogonzag on 2009-11-22
Hola amigos, soy nuevo en esto de ubuntu 9.10 y la verdad es que todo funcionaba de maravilla hasta que descargue Skype 2.1 (beta) para poder entablar una Videoconferencia y no la reconocio, luego entre en las preferencias para configurar la camara y cuando hise la prueba, la imagen se tornó Verde y con algunas rayas negras... googlie por días y la verdad es que probé algunas cosas y una de ellas fue instalar un programa llamado Camorama para ver si detectaba la webcam y la cosa fue peor por que nisiquiera la reconocio y me lanzó un error... bueno... ya no se que hacer y ojalá ustedes me puedan ayudar...

---

### Post by Carlos C on 2009-11-23
En estos casos lo mejor es primero revisar la documentación oficial:

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Se recomienda verificar un par de cosas antes de intentar instalar [EasyCam]("http://translate.google.cl/translate?u=http%3A%2F%2Fprojet.jbtheou.fr%2F&sl=fr&tl=es&hl=es&ie=UTF-8"), que es una herramienta para instalar drivers de webcam.

Saludos.

---

### Post by Italogonzag on 2009-11-23
la verdad es que la camara corre muy bien con Cheese, pero en Skype sigue la pantalla verde... y el Easycam no lo pude instalar :( 
cundo pongo: 
sudo apt-get update, al terminar la descarga sale el siguiente error: 
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY CA5D96E9AB82B686
y luego esto:
italo@italo-laptop:~$ sudo apt-get install easycam2-gtk
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  easycam2-gtk: Depende: python2.4-glade2 pero no es instalable
                Depende: python2.4-gtk2 pero no es instalable
                Depende: easycam2-core pero no va a instalarse
E: Paquetes rotos
Me doy... no se que hacer...

---

### Post by nopersona on 2009-11-24
Las cámaras más o menos antiguas no corren con v4l2. Ubuntu por defecto trae esta configuración. Yo tuve el mismo problema con una 4tech, era asunto de configuración. Lo que hice fue reponer v4l. Me imagino que cuando quieres configurar la cámara se te pega skype. Sería bueno que tiraras el log por terminal para ver. 

```
sudo apt-get install ld.so.preload-manager
``````
sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so
```
Después cambia la opción en la pestaña video por v4l

```
gstreamer-properties
```Ahora ya debería funcionarte la cámara. Puedes reinciar el entrono gráfico para comprobar. 

También hice un script para lanzar Skype en caso de que alguna actualización me rescriba la conficuración. Es muy sencillo:

```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```Le das permisos de ejecución y le pones un icono.  A ver cómo te va. 

P.S.: Si no entiendes algo, no dudes en preguntar.

---

### Post by Italogonzag on 2009-11-24
Lo máximo!! ahora si funciona... que buena :D
GRACIAS... NOperSona 
(ahora solo me falta saber como hacer un "script" para lanzar Skype, pero eso lo puedo investigar yo)

Problema solucionado jejeje!!

---

### Post by Carlos C on 2009-11-24
Me alegro que se solucionara. Sobre el error:
> **Italogonzag said:**
> Easycam no lo pude instalar :( 
cundo pongo: 
sudo apt-get update, al terminar la descarga sale el siguiente error: 
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY CA5D96E9AB82B686


Te faltaba la llave pública. La próxima vez que eso te ocurra puedes mirar acá:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

Saludos.

---

### Post by Italogonzag on 2010-05-09
hola... sabes que ahora le puse ubuntu 10.04 a mi notebook y la camara vieja que tenía la regalé porque me compre una nueva y no me funciona con esta configuración y me gustará saber... cómo puedo volver todo a la normalidad??? 
estoy teniendo problemas con skype, ahora no lo puedo abrir y me arroja este error:
[B][I]
"No se pudo lanzar «Skype» 
Ha ocurrido un error al ejecutar el proceso hijo «bash-c» (No existe el fichero ó directorio)"[/I][/B]

entonces desinstale el programa y luego lo volví a instalar y no pasa nada... me arroja el mismo error siempre.. ojalá me puedan ayudar...

--- Intente cambiar una de las pestañas del "selector de sistemas multimedia" a v4l2 y me arroja otro error... lo abrí desde una terminal con: 
gstreamer-properties[I][B]
"Video for Linux 2 (v4l2): No se puede identificar el dispositivo «/dev/video0»."[/B][/I]




Gracias de antemano!

---

