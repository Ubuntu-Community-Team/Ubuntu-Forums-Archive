---
title: "Problemas Codecs y Video"
date: 2012-06-27
forum: Hardware
---

### Post by deadbrain72 on 2012-06-27
Hola, mi nombre es Pablo y soy nuevo en ubuntu.

Tengo una pc bastante modesta, micro AMD semprom 2800+, placa de video NVidia NV44A [GeForce 6200], 512 de ram, disco de 80gb.

Probe varias distros de linux y me quede con Xubuntu 11.10 que hasta el momento es el que mejor corre en esta PC.

El problema es el siguiente, a ver si alguien me puede ayudar:

Youtube se ve cortado, ni hablar si pongo la pantalla entera.

los videos .mov q bajo de mi camara de fotos, mas lentos aun.

pero todas las pelis, en avi, divx, etc.. corren a la perfeccion.

por ultimo, instale un juego el clasico freedoom, pero al correrlo me dice video incompatible y ya no hay forma de que vuelva a ver nada en la pantalla, debo reiniciar.

este ultimo problema es seguro la configuracion de la placa nvidia, porque la desconecto desde el Bios y dejo la placa onboard y el juego corre...

Asi que si alguien me puede ayudar en estos 2 puntos le estpare muy agradecido.
el tema de la configuracion de la nvidia para correr el juego (tiene solo ese rollo, lo demas todo OK)

Y que hacer con los videos .mov y youtube, esto lei por todos lados.
tengo los restricted codecs
y en los navegadores firefox y chromium, estan instalados en plugins: Remoting Viewer, IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)), 
VLC Multimedia Plug-in, Shockwave Flash - Versión: 10.1 r999.<br>Gnash 0.8.10dev, the GNU SWF Player
de esto ultimo lei por todos lados he instale, desinstale y me marie, pero no obtuve resultados.

1000 gracias por leer esto, saludos
P):

---

### Post by dirty fingers on 2012-07-10
Para youtube la mejor solución es [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

Con los .mov no hay nada que hacer, es un formato de mac que apesta. Convertilos con [http://handbrake.fr/](http://handbrake.fr/)

Y no olvides usar XV como salida de video y poner los driver de nvidia.

pd: gnash sera libre bla bla bla pero anda muy feo. Usa el flash de adobe

---

