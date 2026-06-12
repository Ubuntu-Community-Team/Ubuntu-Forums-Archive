---
title: "Audio 7.1 Asus K8N4-E Deluxe"
date: 2008-12-06
forum: Hardware
---

### Post by viltrop on 2008-12-06
Bueno primero y principal quiero presentarme, me llamo Luis, soy de tucumán

es la primera vez q instalo Ubuntu 8.04 Hardy Heron, me esta funcionando de 10, pude instalar bien los drivers de video y otros programas q fui probando

pero bueno mucho no puedo hacer siendo nuevo en linux :P

lo que necesito es q me den una mano con el audio de mi motherboard, el audio anda pero no se como hacer q funcione en 7.1
mi mother es una asus k8n4-e deluxe

pido disculpas si este tema ya se lo vio en otro thread pero no encontre algo bien explicado

desde ya muchas gracias

---

### Post by Hei Ku on 2008-12-06
Generalmente te lo toma automatico. Que es lo que no te anda?

---

### Post by viltrop on 2008-12-08
no encuentro la forma para q ande, tal vez sea como dices vos, ya lo habra tomado, pero en q parte veo la configuracion o desde donde habilito las otras salidas, x q tengo conectado el equipo de audio 7.1 pero solo funciona el audio comun, dos salidas izquierda y derecha.
como dije antes soy nuevo en ubuntu ](*,), y me cuesta un poquito algunas cosas

---

### Post by Hei Ku on 2008-12-08
Ejecuta alsamixer. Ahi podes ver todos los seteos y si tenes alguna salida con el volumen al minimo, que suele ser lo mas comun.

---

### Post by User21 on 2008-12-09
Tambien puede suceder que no te tome el modulo ideal para activar el 7.1. Yo tuve el mismo [problema con 5.1]("http://ubuntuway.wordpress.com/2008/11/17/sonido-51-en-ubuntu/") en un motherboard ASUS. Lo solucione [**así**]("http://ubuntuforums.org/showthread.php?t=984681"). 
Estate muy atento en la seleccion del modelname, de modo que tome correctamente la cantidad de "jacks" que tengas detras del gabinete. 
Suerte y contanos si lo solucionaste y cómo!

---

### Post by User21 on 2008-12-09
Según las [especificaciones de tu motherboard]("http://ar.asus.com/products.aspx?l1=3&l2=14&l3=172&l4=0&model=454&modelmenu=2") , usa el codec Realtek ALC850, 8-channel CODEC.
Tenés 2 posibilidades:
a1) en un terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```Alli se abre un editor de texto con un archivo. Te vas hasta el final y agregás (o editás, de ya existir), la siguiente linea:
```
options snd-hda-intel model=auto 
```reiniciar y esperar que arranque el sonido 7.1  (siempre y cuando estés probando medios en 8 canales, y no un MP3 que solo tiene 2 canales.

o la otra opcion:
b1)  en un terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```Alli se abre un editor de texto con un archivo. Te vas hasta el final y agregás (o editás, de ya existir), la siguiente linea:
```
options snd-hda-intel model=6stack-dig
``` si tenes 6 clavijias traseras.. o 
```
options snd-hda-intel model=3stack-dig
``` si tenes 3 clavijas traseras.
reiniciar y esperar que arranque el sonido 7.1, siempre y cuando sea verdadero sonido multicanal.

Si aun despues de esto, no funciona, veremos si algun EXPERTO te da una mano.

**ES MUY IMPORTANTE** que estés probando con contenido que cuente con sonido 5.1 o 7.1 (DVD's comerciales o contenido que soporte este tipo de sonido de alta definicion). 
Si estás probando con un MP3, solo tiene 2 canales, y se escucharán en front left y front right. Si queres duplicar o cuadriplicar el sonido stereo en los otros parlantes, hay un[** tutorial**]("http://ubuntu-ar.org/soporte/comos/reproducir-sonidos-de-dos-canales-en-4-o-6-canales") en el sitio de ubuntu-ar.
Tambien tenes que activar, en el administrador de sonido de Gnome, el sonido de 4, 6 u 8 canales y sus correspondientes controles de volumen.

Saludos.

---

### Post by viltrop on 2008-12-12
hola disculpa q no haya contestado, tuve un pequeño problema con la computadora, hubo una tormenta electrica y me rompio la fuente cuando hubo una suba de tension, apenas pueda cambiarle la fuente y logre encender la compu a ver si no se me rompio nada mas, pruebo y les digo, gracias :(

---

