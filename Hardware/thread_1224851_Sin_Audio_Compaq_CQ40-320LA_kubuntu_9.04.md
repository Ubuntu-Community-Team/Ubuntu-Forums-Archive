---
title: "Sin Audio Compaq CQ40-320LA kubuntu 9.04"
date: 2009-07-27
forum: Hardware
---

### Post by AlbertoC on 2009-07-27
estimados necesito ayuda:

Tengo en notebook Compaq presario CQ40-320LA.
Soy usuario nuevo de kubuntu, he instalado el programa, todo a funcionado bien, pero no funcionan los parlantes integrados (no emiten sonido), solo funciona la salida de audifonos.
he leido muchisimo, pero en ningun lado hablan sobre como darle solucion al problema.
Utiliso kubuntu 9.04
escribiendo en el terminal aplay-l me sale la siguiente informacion:

tarjeta 0: SB [HDA ATI SB], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

Los volumenes estan al maximo tengo audio por la salida de audifonos, pero no tengo audio en los parlantes integrados.
porfavor ayudenme.

Agradecido por su tiempo
ATTE 
AlbertoC

---

### Post by Carlos C on 2009-08-14
Hola. Acá te pongo un enlace en donde al parecer solucionan el problema de audio para el modelo de laptop que tienes:

[http://www.chilecomparte.cl/index.php?showtopic=834991](http://www.chilecomparte.cl/index.php?showtopic=834991)

Saludos.

---

### Post by keithgc29 on 2009-09-09
hola, que tal ... no se si aún tengas este problema con tu tarjeta de sonido, pero tengo el mismo modelo de notebook que tú, y resolvi el problema de está forma.
1. edito el archivo del controlador alsa...
sudo gedit /etc/modprobe.d/alsa-base.conf

2. al final del archivo ingreso esta línea
options snd-hda-intel model=hp-m4

3. reinicio el equipo ...

con estó mi altavoces funcionan ...
espero haberte podido ayudar ... 
saludos.

---

### Post by japjosea89 on 2010-02-21
> **keithgc29 said:**
> hola, que tal ... no se si aún tengas este problema con tu tarjeta de sonido, pero tengo el mismo modelo de notebook que tú, y resolvi el problema de está forma.
1. edito el archivo del controlador alsa...
sudo gedit /etc/modprobe.d/alsa-base.conf

2. al final del archivo ingreso esta línea
options snd-hda-intel model=hp-m4

3. reinicio el equipo ...

con estó mi altavoces funcionan ...
espero haberte podido ayudar ... 
saludos.

MIL GRACIAS HERMANO!!! mi sonido esta funcionando a la perfeccion! yo sabia que la solucion mas sencilla era la mejor. muchas gracias.:D

---

### Post by Carlos C on 2010-02-22
Lo doy por resuelto entonces. Si el autor del post manifiesta que no es así lo cambiamos, pero es bueno registrar que existe una manera de arreglarlo.

Saludos.

---

