---
title: "Creative Webcam III en Intrepid/Jaunty"
date: 2009-04-08
forum: Hardware
---

### Post by santiagoward2000 on 2009-04-08
Gente, vengo con un problema que recién me entero que existe (si tardé 6 meses, imagínense la bola que le doy). Tengo una Creative Webcam III, y no anda ni en Intrepid ni en Jaunty Beta. La probé con Ekiga, Cheese, Camorama y Kopete, y hasta con gstreamer-properties, y nada (en Cheese y gstreamer-properties puedo ver rayas de colores, como en la tele, con un cuadradito con lluvia).
Cuando trato de correr en **gstreamer-properties** con v4l o v4l2, me dice: > Could not open device "/dev/video0" for reading and writing.
Pero el kernel la detecta. **lsusb** me da: > Bus 001 Device 005: ID 05a9:0511 OmniVision Technologies, Inc. OV511 WebCam
Estuve buscando, y encontré unos cuantos bugs reportados de esto, pero ninguna solución. ¿Alguna idea?

_PS:_
Por si preguntan, en realidad me di cuenta que no funcionaba cuando probaba Jaunty, para ver qué anda y qué no. Nunca la había probado en Intrepid antes. En Hardy andaba lo más bien, pero nunca la usé para nada útil. Esto es más como reto, a ver si la puedo hacer andar, pero hasta ahora me gana :lolflag:

---

### Post by krcabrer on 2009-05-03
Reciba un cordial saludo de Colombia
santiagoward2000

Quisiera saber si ya pudiste solucionar el problema, porque yo también tengo
el mismo problema en donde con el Hardy Heron me funcionaba muy bien...

Pero me pasé al intrepid y no sé que pasó.

Muchas gracias por tu ayuda.

Kenneth

---

### Post by santiagoward2000 on 2009-05-10
> **krcabrer said:**
> Reciba un cordial saludo de Colombia
santiagoward2000

Quisiera saber si ya pudiste solucionar el problema, porque yo también tengo
el mismo problema en donde con el Hardy Heron me funcionaba muy bien...

Pero me pasé al intrepid y no sé que pasó.

Muchas gracias por tu ayuda.

Kenneth

Saludos Kenneth,
Perdón por no haber respondido antes.
No, no pude resolverlo. Tampoco estuve investigando mucho. Encontré algunos reportes de bug, pero no cómo hacerla andar.
Saludos!

---

### Post by faktorqm on 2009-05-13
yo tengo la misma y la unica manera de hacerla andar que encontre, fue con el programa wxcam 0.96 y con el vlc, que por supuesto no podes hacer nada. El wxcam va perfecto, filma y saca fotos. Aclaro que uso ubuntu 8.04 actualizado a la fecha, mi webcam es USB, y tambien me la detecta como Omnivision blablabla. Si no les anda posteo yo todas las cosas que necesiten, salu2!

---

### Post by santiagoward2000 on 2009-05-13
> **faktorqm said:**
> yo tengo la misma y la unica manera de hacerla andar que encontre, fue con el programa wxcam 0.96 y con el vlc, que por supuesto no podes hacer nada. El wxcam va perfecto, filma y saca fotos. Aclaro que uso ubuntu 8.04 actualizado a la fecha, mi webcam es USB, y tambien me la detecta como Omnivision blablabla. Si no les anda posteo yo todas las cosas que necesiten, salu2!

Probé con el wxcam 1.04, pero no anduvo. Me dice: > Cannot open /dev/video0.
Please check if your system has the correct driver for your webcam, or change the webcam device in settings->preferences.
Estuve buscando el 0.96, a ver si con ese andaba, pero no lo encontré por ningún lado.
Además, es raro que a vos solo te ande con el wxcam en Ubuntu 8.04. Cuando lo usaba (como hace 6 meses) me andaba en cualquier programa.
Saludos!

---

### Post by juancarlospaco on 2009-05-13
**ls /dev/video***

*a veces se llama /dev/video a secas y los programas buscan /dev/video0 y no la encuentran.*

---

### Post by santiagoward2000 on 2009-05-14
> **juancarlospaco said:**
> **ls /dev/video***

*a veces se llama /dev/video a secas y los programas buscan /dev/video0 y no la encuentran.*

> ls /dev/video*
/dev/video0


No, ahí está, en /dev/video0. Lo que me está pareciendo es que hay algún problema con los permisos de uso. Cuando corro **gstreamer-properties** y pruebo el plugin **v4l**, en la consola sale: > gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not open device "/dev/video0" for reading and writing. [v4l_calls.c(179): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc3:
system error: Permission denied]
Entonces probé correrlo con sudo, y ahí algo se ve, en una imagen re chica y con cuadrados de colores saltando encima, pero de fondo puedo verme. No se distingue del todo, pero si paso la mano cerca se ve bastante bien (atrás de todos los colores).
Saludos!

---

### Post by no2498 on 2009-09-14
gstreamer-properties


click video try vl42 or vl41 an test

---

### Post by santiagoward2000 on 2009-09-16
> **no2498 said:**
> gstreamer-properties


click video try vl42 or vl41 an test

Hi no2498!
As I said before, trying both drivers results in:
**_v4l:_** > Video for Linux (v4l): Could not open device "/dev/video0" for reading and writing.
**_v4l2:_**> Video for Linux 2 (v4l2): Could not open device '/dev/video0' for reading and writing.

A los de acá, espero sepan disculpar que haya contestado en inglés. No lo traduje porque estaría repitiendo lo que dije en el primer post. Ya que estoy, cuento que mientras estuve probando karmic, esta webcam anduvo sin problemas, por los que supongo que solo hay que esperar.
Saludos!

---

### Post by Hei Ku on 2009-09-16
Probablemente. El v4l paso por algunos cambios para la epoca de la 9.04 y no todos los programas actualizaron a tiempo. Habia unos bugs con comentarios bastante graficos sobre el tema. Que no ande Skype esta relacionado a esto.

---

