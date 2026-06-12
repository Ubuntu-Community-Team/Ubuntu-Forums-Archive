---
title: "Flash + ubuntu 9.04 + pantalla completa = lag"
date: 2009-09-08
forum: Hardware
---

### Post by verahert on 2009-09-08
El problema que estoy teniendo es que cuando reproduzco en youtube un video si lo pongo en pantalla completo, se ve lento con el sonido entrecortado; probe las 3 soluciones de esta web: 

[http://www.tuxapuntes.com/drupal/node/1372]("http://www.tuxapuntes.com/drupal/node/1372")

pero no hay caso, el problema persiste.

tengo una hd3200(780g) (onboard) SIN el controlador privativo, con el driver que trae ubuntu.

Alguna idea?

Saludos, Nicolás.

---

### Post by Hei Ku on 2009-09-08
Instala el driver privativo. El driver libre no anda bien para los modelos HD de ATI.

---

### Post by verahert on 2009-09-08
El problema es que si instalo el driver privativo, la reproduccion de HD con xv en SMPlayer anda terriblemente mal, no asi si lo hago con el driver libre que viene por defecto, como puede ser?

Saludos, Nicolás.

PD: en una pc con atlhon xp y geforce 2 (drivers libres), ubuntu+flash anda como en mi pc, es decir laggeado :S

---

### Post by Hei Ku on 2009-09-09
Hay que agregarle algunas opciones al xorg.conf para que el video ande bien.

VideoOverlay y otras que recomiendan en la wiki de ATI.

---

### Post by verahert on 2009-09-09
En la pc con la nvidia gf2 instale los drivers 96.43.10, y el problema en youtube persiste en fullscreen, como puedo hacer para q funcione en nvidia?

---

### Post by guillermolisi on 2009-09-09
> **verahert said:**
> En la pc con la nvidia gf2 instale los drivers 96.43.10, y el problema en youtube persiste en fullscreen, como puedo hacer para q funcione en nvidia?
En este thread resolvamos el problema sobre la ATI y si necesitas tambien hacerlo sobre una nVidia, hay otros threads que hablan sovre el tema, pero va en thread aparte.

---

### Post by verahert on 2009-09-10
Hola nuevamente, finalmente instale la version 9.8 manualmente del driver de ati con la guia de wiki ati, y el flash, asi como el XV + Smplayer funcionan correctamente, el problema que estoy teniendo ahora es que tengo Video Tearing (lineas horizontales), intente solucionarlo activando el Vsync en el panel de ati y en el compiz (tengo el compiz activado), pero no hay caso las lineas siguen :/, con el compiz desactivado sigo igual.

alguna idea?


Saludos Nicolás.

---

### Post by Hei Ku on 2009-09-10
Tenes bien configurado el refresco? En el Catalyst podes configurar que ajuste el refresco al monitor justamente para evitar ese problema.

---

### Post by verahert on 2009-09-10
no, no lo cambie, mi monitor es de 20"@1680x1050 60hz, si quiero configurar el refresco en el panel de ati, la parte del monitor esta gris (no puedo cambiar las opciones) que puede ser?

---

### Post by Hei Ku on 2009-09-10
No es el refresco del monitor, si no la opcion que dice ajustar el refresco de la placa al refresco del monitor.

---

### Post by verahert on 2009-09-12
la verdad que no encuentra esa opción que decís, como habilito eso?

Saludos, Nicolás.

---

