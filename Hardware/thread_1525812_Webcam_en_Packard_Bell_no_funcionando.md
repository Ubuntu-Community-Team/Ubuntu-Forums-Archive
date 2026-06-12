---
title: "Webcam en Packard Bell no funcionando"
date: 2010-07-07
forum: Hardware
---

### Post by SLA_leandrin on 2010-07-07
Hola a todos,

He googleado bastante pero no he encontrado la solución al problema que planteo aquí, estoy perdiendo un poco la esperanza, así que recurro a vuestro infinito conocimiento linuxero.

He instalado Lucid en una notebook Packard Bell, y me anduvo todo ok (Bue, salvo por la placa ATI pero eso es conocido, de todos modos anda). El tema es que estuve tratando de utilizar la webcam recién estos días, la webcam es la siguiente;


```
0402:5602 ALi Corp. Video Camera Controller
```

Por lo que he leído, debiera andar con el driver gspca_m5602. Esto ya está instalado y cargado en el kernell;


```
$ lsmod | grep gspca
gspca_m5602            51833  0 
gspca_main             21199  1 gspca_m5602
videodev               34361  1 gspca_main
```

En gstreamer-properties la detecta bien, con v4l2.
PERO: al correr cualquier programa que use la cámara (Cheese, Skype) la imagen es siempre negra. Sin importar si los corro con el ya famoso comando;

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
``` 

ó

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 

```
Además, Dr. Google me devuelve este inquietante bug en launchpad;

[https://bugs.launchpad.net/ubuntu/+bug/350382]("https://bugs.launchpad.net/ubuntu/+bug/350382")

Es posible que haya llegado a un punto muerto?

Desde ya amigos, muchas gracias.

Saludos,
Leandro.

---

### Post by SLA_leandrin on 2010-07-10
Nada no?

---

### Post by utilitytrack on 2010-10-23
Hi! Exactly your problem is described here: [https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575") 
You feel free to add your own experience, comments, logs, etc.

---

### Post by Pan0ramix on 2010-10-31
Nada no? Si, el tema de las webcams es un talón de Aquiles en Linux... No hay uno que se ponga las pilas con el tema, digo yo? Si entendiera algo ya me hubiera puesto a meter mano, pero la verdad que cada vez entiendo menos cómo funciona esto.
seguiremos esperando que "se nos abra el arco"

---

### Post by hectorivand on 2010-11-01
> **Pan0ramix said:**
> Nada no? Si, el tema de las webcams es un talón de Aquiles en Linux... No hay uno que se ponga las pilas con el tema, digo yo? Si entendiera algo ya me hubiera puesto a meter mano, pero la verdad que cada vez entiendo menos cómo funciona esto.
seguiremos esperando que "se nos abra el arco"

Hola Panoramix, a otra persona le conteste lo mismo, no es un problema del sistema si no de los fabricantes de hardware que no hacen productos compatibles con linux.

La comunidad hace lo posible para que ciertas cosas funcionen, pero en algunos casos se llega al extremo de que al ser algo tan cerrado, no se logra que funcione.

Saludos
Nacho

---

### Post by Pan0ramix on 2010-11-01
Gracias por tu respuesta, Nacho.
 
Espero que el desafío planteado lo tome alguien para que lo haga funcionar. Si llegado el caso, siempre extiendo un donativo para ellos. Asi lo hago a menudo con desarrollos que encuentro muy útiles y valorados en consecuencia.

---

