---
title: "Problema con Perifericos en Karmic"
date: 2009-12-18
forum: Hardware
---

### Post by daggaz on 2009-12-18
Hola.
Bueno, la cosa es que ya llevo unas semanas usando Karmic y aunque he logrado solucionar algunos de los problemas todavía hay varias cosas que no se solucionan aunque actualice.
Creo que la peor de todas es que Ubuntu no reconoce de forma «automática» mis periféricos, y con esto me refiero a mi lector y quemador de DVD a las* tarjetas SD* y los *Pendrives USB*, a mi cámara fotográfica *Canon EOS Rebel*, a mi teclado *MIDI M-Audi*o, mi *Tablet Genius Mousepen* y en general creo que lo que sea le conecte no lo va a querer leer por las buenas.
Hace unos días me urgía copiar unos archivos y logré montar un *Pendrive USB* desde la terminal, con «fstab» y «mount» si no mal recuerdo. El caso es que al parecer los puertos sí reconocen que hay algo conectado pero no dan ese amigable mensaje de «¿Que desea hacer con lo que conectó o insertó?». Es más, no puedo ni montar la cámara o un USB, manualmente ni el MIDI mas que por medio de la terminal y aún así me da muchos problemas, igual que la ver un DVD, se vuelve una tarea terrible y absurda por que la unidad se desmonta cada vez y solo puedo ejecutar las películas en el reproductor que viene por default en Ubuntu, el VLC no funciona bien ahora.

Mi «sudo fdisk -l» dice:

```
Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf6df09df

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         255     2048256   82  Linux swap / Solaris
/dev/sda3             256       38913   310520385    5  Extendida
/dev/sda5            4117       38913   279506871   83  Linux
/dev/sda6             256        4116    31013419+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco
```Mi «sudo gedit /etc/fstab» dice:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1dcd2ec4-30c6-4fbc-a248-d7b6e879d09d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=41ae427f-6e60-497a-995b-a1978c64f56f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Todo esto empezó al actualizar a Karmic... Y hay otro problema que no sé si tenga relación con este; algo pasa con el idioma que está mezclado inglés y español, ya traté de arreglarlo pero creo que es un problema de la actualización. La cosa es que por ejemplo, si trato de abrir Nautilus desde el menú, en vez de decir «Equipo» dice «Computer» y al tratar de abrirlo me dice: 


> No se pudo mostrar «computer:».
Nautilus no puede manejar lugares «computer».
...y también tengo la sospecha de que la swap no está bien.


Espero me puedan ayudar, gracias.

---

### Post by daggaz on 2009-12-23
He estado buscando en foros y el problema parece estar presente con varios tipos de periféricos, sobre todo los conectados vía USB, la cosa es que la mayoría nota el problema con los *Pendrives* pero no sé si utilicen más periféricos como en mi caso. Pero todas las soluciones parecen ser montar desde la terminal, cosa poco cómoda tratándose por ejemplo de mi teclado MIDI o de la cámara, no quiero hacer eso cada vez que conecto algo al PC... Lo que más me molesta es que eso no me pasaba en Jaunty ¿qué fue lo que cambió en Karmic en este aspecto de los periféricos?
Espero que alguien sepa como solucionar este problema de raíz y me pueda ayudar, estaré muy agradecido; prefiero no tener que volver a Jaunty.

---

