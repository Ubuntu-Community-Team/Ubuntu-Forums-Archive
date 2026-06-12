---
title: "problemas para detectar webcam eye 312 en ubuntu 9.04"
date: 2009-08-05
forum: Hardware
---

### Post by wos977 on 2009-08-05
instale el 9.04 y anda todo 10 puntos a excepcion de la webcam genius eye 312. alguien podria ayudarme.  gracias

---

### Post by guillermolisi on 2009-08-05
Fijate que [en este post]("http://ubuntuforums.org/showpost.php?p=7323077&postcount=2"), de un thread tambien referido a webcams Genius pero sobre otro modelo, hay dos hipervinculos en donde podes verificar si esa camara esta soportada o no.

---

### Post by wos977 on 2009-08-05
> **guillermolisi said:**
> Fijate que [en este post]("http://ubuntuforums.org/showpost.php?p=7323077&postcount=2"), de un thread tambien referido a webcams Genius pero sobre otro modelo, hay dos hipervinculos en donde podes verificar si esa camara esta soportada o no.


te agradezco muchisimo pero no figura la webcam en ninguna de las 2 listas :(

---

### Post by x_jefesin_x on 2009-10-04
Hace un tiempo que me compre la misma webcam, y ahora leyendo esta lista [http://www.kernel.org/doc/Documentation/video4linux/gspca.txt](http://www.kernel.org/doc/Documentation/video4linux/gspca.txt) veo que esta, supuestamente,  soportada por los drivers. No es asi?. Como puedo instalar esos drivers?

De antemano muchas gracias;-)

Saludos...

PD: Uso ubuntu 9.04

---

### Post by faktorqm on 2009-10-05
en la terminal:

```
sudo modprobe gspca_pac7311
```

fijate si anda eso. salu2!

---

### Post by ramiro_md on 2009-10-15
Aviso, para que no pierdan las epseranzas aquellos que no han  hecho funcionar la camara, que la cámara ya está soportada. 
En mi Debian por lo menos yo la puedo usar. Actualizen el kernel a la última versión e instalen la última versión de los drivers.
Saludos !

---

### Post by ramiro_md on 2009-11-09
Man fijate que si estás usando la versión 9.10 de ubuntu te debería andar la camara sin problemas. Instala cheese y fijate si ese programa te toma la cam, porque yo estoy usando ese y no hice más que instalarlo y ejecutarlo.
Un saludo y suerte !

---

### Post by x_jefesin_x on 2009-12-05
estoy usando ubuntu 9.10 pero aun no se ve bien se me ve al cabeza abajo y a una muy baja calidad para ver la webcam use cheese...

alguna idea????

Saludos ):P

---

### Post by Mauro22 on 2009-12-05
Lo de cabeza abajo lo podes solucionar con el mismo cheese, aunque no tiene sentido si los programas donde la uses tienen la opcion de voltear la imagen..
En Cheese tenés en el boton "efectos": Giro Horizontal y Giro Vertical.


La perdida de calidad, te refieres a como se ve en Wind*ws ??

---

### Post by guillermolisi on 2010-02-14
> **rojojuan said:**
> Tengo que instalar una webcam en Ubuntu 9.10. Alguien compró alguna que ande bien en Capital Federal?
La pregunta es para tener la certeza que funcione bien y sin problemas.
Gracias desde ya por la ayuda
Movido a un [thread nuevo]("http://ubuntuforums.org/showthread.php?t=1406771") en Comunidad

---

