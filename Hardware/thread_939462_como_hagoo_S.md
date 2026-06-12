---
title: "como hagoo :S?"
date: 2008-10-05
forum: Hardware
---

### Post by francosp on 2008-10-05
hola tengo el siguiente problema:
cuando inicia el ubuntu en lugar de aparecer el escritorio aparece el modo texto del devian...me dicen que comandos tengo que escribir?

...gracias

---

### Post by Hei Ku on 2008-10-06
eso es porque te fallo algo en el driver de video. Que drivers usaste o que cambiaste antes que te sucediera info?

---

### Post by sajnox on 2008-10-06
Podemos probar con algo facil

1) Backup del xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

2) Reconfiguramos el xorg.conf

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3) Arrancamos el server grafico

```
startx
```

Si funciono, problema resuelto!!

No funciono, volvemos para atras y dejamos como estaba

```
sudo mv /etc/X11/xorg.conf.back /etc/X11/xorg.conf
```

Y lamento que no lo haya arreglado

---

### Post by rober-mpp on 2008-10-06
$ startx 

y a ver que pasa...

Suerte con eso.

---

### Post by pol666 on 2008-10-06
actualizaste kernel?

---

### Post by francosp on 2008-10-06
hola tengo el siguiente problema:
cuando inicia el ubuntu en lugar de aparecer el escritorio aparece esto

Busybox v.1.1.3 (debian 1:1.3-5ubuntu12) built-in shell (ash)

(initransf)


.......gracias

---

### Post by pablo.s on 2009-03-08
Hola: Está mal instalado, por eso te sale ese mensaje. Probablemente tiene un
conflicto con el disco donde lo instalaste. Por lo que veo no es un problema de
drivers de video.

Saludos

---

### Post by leonardo83 on 2009-03-08
> **francosp said:**
> hola tengo el siguiente problema:
cuando inicia el ubuntu en lugar de aparecer el escritorio aparece esto

Busybox v.1.1.3 (debian 1:1.3-5ubuntu12) built-in shell (ash)

(initransf)


.......gracias

a mi me paso lo mismo cuando loquiese instalar, no se que problema tenia y probe todo lo que me dijeron aca.
Al final probe reinstalandolo varias veces y se arreglo.
Me dijeron q es un problema de instalacion, era raro porque a mi me pasaba apenas queria probar el live cd, es decir, sin instalarlo!
Te recomiendo probarlo de esa forma a ver si levanta o sino reinstalando a ver si se soluciona. Saludos! :D

---

