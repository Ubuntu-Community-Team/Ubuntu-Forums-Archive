---
title: "[SOLUCIONADO] Problema con sonido Ubuntu 9.04"
date: 2009-06-29
forum: Hardware
---

### Post by Naldylipu on 2009-06-29
Hola
hoy actualicé el sistema y me quedé sin audio, hasta antes de la actualización todo funcionaba bien, ahora solo escucho un ruido como el de cables mal conectados pasando corriente, probé cambiando las preferencias de sonido y solo logré escuchar un pitido
Es un Vaio VGN-NR350FE
82801H (ICH8 Family) HD Audio Controller 
HDA Intel Sound Card 
Ojala puedan ayudarme :)

---

### Post by moreback on 2009-06-30
Pegar salida de ```
aplay -l
```

Revisar en Sistema -> Preferencias -> Sonido

Revisar también Sistema -> Preferencias -> Selector de sistemas multimedia

---

### Post by Naldylipu on 2009-06-30
Al hacer lo que me dices me sale esto
```
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC262 Analog [ALC262 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```
 
Y no me aparece en Sistema>Preferencias> Selector de sistemas multimedia :S

---

### Post by moreback on 2009-06-30
Revisa en Sistema -> Preferencias -> Sonido y prueba con PulseAudio o con esa tarjeta que te aparece.

---

### Post by Naldylipu on 2009-06-30
Ahi funcionó, muchas gracias ;)

---

### Post by moreback on 2009-06-30
genial!

/me se gana los porotos :-)

---

