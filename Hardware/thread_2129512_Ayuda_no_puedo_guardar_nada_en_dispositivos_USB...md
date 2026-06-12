---
title: "Ayuda: no puedo guardar nada en dispositivos USB.."
date: 2013-03-26
forum: Hardware
---

### Post by sibilin on 2013-03-26
Hola:

Primero que que todo, soy nueva en el foro espero poder aprender más de Ubuntu.
Ahora tengo un problemas o menos en mi PC  ( es un  viao  vaio vpcm120al) un  modelo que no tiene lector de CD.
y en mi computador instalé  Ubuntu 12.01 desde hace un año.
El asunto es que no puedo respaldar mi archivos en mi disco duro externo, porque me aparece el siguiente mensaje  " error no hay espacio en el disco" ko curioso es que lo he formateado (500 GB) y aún asi me sigue apareciendo el mismo error. con mis pendrive de menor capacidad me ocurre lo mismo.
¿qué puedo hacer?
de antemano agradezco su lectura y ayuda.:KS:KS

---

### Post by asterix77 on 2013-03-27
Deberías entregar un poco más información de tu problema, dices que tienes 12.04 desde hace un año, ¿significa eso que el problema lo tienes desde entonces ,o solo es desde hace poco?. Con nautilus ¿puedes abrir tu disco duro externo y ver su contenido (me imagino que tiene algún contenido)?. Dices que lo formateastes, pero ¿con que utilidad y que formato le distes?

Por último abre una terminal y pega el contenido de lo siguiente (con el dispositivo usb conectado)

$sudo fdisk -l

y luego

$df -h

y finalmente

$lsusb


Saludos

---

