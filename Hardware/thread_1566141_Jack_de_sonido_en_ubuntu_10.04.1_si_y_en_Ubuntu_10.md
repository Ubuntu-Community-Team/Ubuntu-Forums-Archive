---
title: "Jack de sonido en ubuntu 10.04.1 si y en Ubuntu 10.04 no"
date: 2010-09-02
forum: Hardware
---

### Post by krackmu on 2010-09-02
Hola...

A que se debe esto?...

Instale ubuntu 10.04 desde el CD, pero hace como hace 2 dias, baje Kubuntu y Ubuntu con la ultimas actualizaciones de mantenimiento (10.04.1), y pasa el que audio que antes me daba problemas ahora funciona **casi** excelente.

El note no me regula el volumen de 0 a 100% sin pasar por toda la escala, calculando mas menos al llegar como al 15% llega al 100%, o sea, si presiono desde el minimo 3 veces ya llega al maximo y en la barra esta casi al minimo, eso lo solucione de una manera x...

pero probando esas versiones desde un pendrive, funciona casi sin problemas, hasta los Jack de los audifonos funcionan, cosa que actualmente no pasa.

Cabe destacar que tengo la version instala actualizada.

Gracias...

---

### Post by Carlos C on 2010-09-02
Hola. Por favor, la próxima vez que desees publicar una duda en el foro te pido que lo hagas en el subforo adecuado. Si no tienes muy clara la división que utilizamos puedes leer el siguiente post:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

También te pido que leas las normas que intentamos aplicar en el foro para que tu experiencia en el mismo sea más efectiva:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Respecto a tu problema, dices que cuando utilizas Ubuntu desde un pendrive el sonido funciona correctamente, en cambio, en el sistema que tienes instalado en tu equipo el volumen no varía de manera certera. Tiene que ser un problema de configuración. Para empezar a buscar más información necesitamos el modelo exacto de tu tarjeta de sonido. Por favor, escribe en el terminal:
```
lspci
```
y copia acá lo que te aparece.
Saludos.

---

### Post by krackmu on 2010-09-03
Este es el modelo de la tarjeta de sonido:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

Como dije en un comienzo, logre el control de volumen, ahora funciona. Lo que me aqueja es el Jack de los audifonos, al ponerlos se corta el audio como corresponde, pero no se escucha en estos.... ese es el problema. y cuando le doy volumen (con los audifonos) se escucha en ambos, en los parlantes del note y en los audifonos.

Saludos.

PD: debo admitir que no escribo acá desde hace tiempo, desde que era foros.ubuntu-cl.org ene tiempo.

---

### Post by RafaelG on 2010-09-04
krackmu,

Segun lo explicado por CarlosC el Post sera Movido al Subforo correspondiente.

Ahora en relacion al inconveniente que tienes podrias verificar con PULSEAUDIO si tienes bien configurado cual es tu Output por Default y cuales son los secundarios.

Saludos!

---

### Post by krackmu on 2010-09-06
> **RafaelG said:**
> krackmu,

Segun lo explicado por CarlosC el Post sera Movido al Subforo correspondiente.

Ahora en relacion al inconveniente que tienes podrias verificar con PULSEAUDIO si tienes bien configurado cual es tu Output por Default y cuales son los secundarios.

Saludos!

Hola.

No tengo idea de como verificarlo la verdad.

Aunque la pregunta era otra de todas maneras. Quiero saber porque pasa en uno y en el otro no.

Saludos.

---

### Post by Carlos C on 2010-09-06
Tengo una duda, dices que arreglaste el problema del volumen ¿Podrías decirnos cómo lo hiciste? Otra duda que tengo es si has modificado de alguna forma tu archivo /etc/modprobe.d/alsa-base.conf.

Saludos.

---

