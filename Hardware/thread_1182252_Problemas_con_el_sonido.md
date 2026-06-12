---
title: "Problemas con el sonido"
date: 2009-06-08
forum: Hardware
---

### Post by raulitro_xD on 2009-06-08
HOla a todos, bueno cuento lo que me pasa.

tengo instalado el ubuntu 9.04, y el sonido funciona, pero pasa que cuando produzco el sonido a traves de los archivos tipo .swf, y depues el sonido no sigue funcionando.

por si les serviria de ayuda
las caracteristicas de la tarjeta del sonido es:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

product: 82801I (ICH9 Family) HD Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 03
wdth: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel

¿que puedo hacer para solucionarlo?

---

### Post by CdK1 on 2009-06-08
Pués es problema de flash, yo que tú haria una de dos, o cambiar de navegador -Opera no te da ese problema, ya lo probé- o de pluggin, de todas maneras si te pasa eso, como root ejecuta:

alsa force-reload y se arregla ;)

---

### Post by pagondel on 2009-06-08
```
sudo aptitude install flashplugin-nonfree-extrasound
```

Saludos!

---

### Post by CdK1 on 2009-06-08
Es que eso también depende del plugin que usa.., además eso no pasa con Opera...

---

### Post by moreback on 2009-06-08
Usen PulseAudio como salida, resuelve muchos problemas.

---

### Post by kamus on 2009-06-09
> **raulitro_xD said:**
> HOla a todos, bueno cuento lo que me pasa.

tengo instalado el ubuntu 9.04, y el sonido funciona, pero pasa que cuando produzco el sonido a traves de los archivos tipo .swf, y depues el sonido no sigue funcionando.

por si les serviria de ayuda
las caracteristicas de la tarjeta del sonido es:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

product: 82801I (ICH9 Family) HD Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 03
wdth: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel

¿que puedo hacer para solucionarlo?

Estas ocupando Firefox ?, puedes reproducir otros archivos de audio?

Saludos

---

### Post by CdK1 on 2009-06-09
alsa force-reload aunque no es la idea..

---

