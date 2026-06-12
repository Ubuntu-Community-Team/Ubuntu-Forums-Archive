---
title: "sonidos raros de sobresaturaciones"
date: 2009-12-07
forum: Hardware
---

### Post by drazhe on 2009-12-07
Hola, luego de la ultima actualización de Ubuntu, comencé a notar que el audio de mi portátil tenia sonidos de sobre saturación cada vez que subía o bajaba el volumen o hacia algo relacionado con el audio de la misma, no me refiero a las frituras obvias del sobre volumen mientras uno escucha música, sino que al subir o bajar el volumen del sistema, sin tener nada de audio o video en reproducción, de los bafles salen unos ruidos de explosiones sobre saturadas.... 
a alguno de ustedes le sucede lo mismo? y por favor! como solucionarlo... porque si sigue así, me van a reventar los bafles de la portátil!

---

### Post by aledruetta on 2009-12-07
> **drazhe said:**
> Hola, luego de la ultima actualización de Ubuntu, comencé a notar que el audio de mi portátil tenia sonidos de sobre saturación cada vez que subía o bajaba el volumen o hacia algo relacionado con el audio de la misma, no me refiero a las frituras obvias del sobre volumen mientras uno escucha música, sino que al subir o bajar el volumen del sistema, sin tener nada de audio o video en reproducción, de los bafles salen unos ruidos de explosiones sobre saturadas.... 
a alguno de ustedes le sucede lo mismo? y por favor! como solucionarlo... porque si sigue así, me van a reventar los bafles de la portátil!

En mi portátil no sucede, pero en la portátil de otra persona que le instalé Karmic, sí. Y no únicamente cuando se manipula el volumen del sistema; a veces lo hace sin razón aparente o simplemente por mover el puntero con el touchpad. Y aclaro que no lo hace desde la última actualización, sino desde momento en que instalé el sistema. Creo que con el paso del tiempo lo está haciendo menos, pero no puedo asegurarlo.

---

### Post by sebastianabate on 2009-12-08
A lo mejor no tiene nada que ver, pero a mi me pasaba algo parecido cada vez que reproducía algún sonido (sea de un video, de un mp3 o de algún alerta de programa), en el momento en el que la reproducción comenzaba. Y buscando un poco encontré que es común con las placas que usan el módulo snd-hda-intel (yo tengo una ALC883 on-board), que en Karmic se carga con opciones de power save que producen estos ruidos.

Lo único que hice fue comentar en el archivo /etc/modprobe.d/alsa-base.conf la línea "options snd-hda-intel power_save=10 power_save_controller=N" (que en mi caso estaba al final del archivo), reiniciar, y santo remedio.

Pero en una notebook (yo tengo una Desktop) no sé si comentar esta línea no generará mayor consumo de batería, dado que la placa de sonido nunca se deshabilita.

---

### Post by alfplayer on 2009-12-08
Esto parece estar relacionado con este hilo: [http://ubuntuforums.org/showthread.php?p=8419677](http://ubuntuforums.org/showthread.php?p=8419677)

Recuerdo haber leído que una posible causa de este problema de "explosiones" son los drivers del hardware de sonido.

---

