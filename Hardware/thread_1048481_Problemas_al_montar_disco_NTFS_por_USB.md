---
title: "Problemas al montar disco NTFS por USB"
date: 2009-01-23
forum: Hardware
---

### Post by KaKuS on 2009-01-23
Hola señores, hace poco debido a que me la paso clonando, reparando y viendo discos sata todo el tiempo me compre un Dock USB Thermaltake (BLACX). El mismo es un simple adaptador de SATA a USB como el que viene en los discos externos, y al principio funciono bien. Colocaba el disco, encendía la fuente y me montaba la unidad automáticamente como un disco extraíble. Pero ahora me da este error:

"No se puede montar el volumen.

Detalles
Mount is denied because setuid and setgid root ntfs-3g is insecure with the external FUSE library. Either remove the setuid/setgid bit from the binary or rebuild NTFS-3G with integrated FUSE support and make setuid root.
Please see more information at http://ntfs-3g.org/support.html#unprivileged"

Fui al URL e intente los pasos, pero o va mas lejos que mis pobres conocimientos o estoy haciendo algo mal. Los datos de mi sistema están en mi firma. Si me pongo a jugar con la utilidad "Dispositivos de almacenamiento" (Ubuntu) lo logro montar pero la idea es que sea automático como al principio.

---

### Post by KaKuS on 2009-01-26
Ahora no me monta automaticamente los pendrives que conecto, al conectar un pendrive me dice:

> No se puede montar el volumen

No es posible montar el volumen <<Nombre del Pen>>

Detalles

mount: sólo el usuario root puede montar /dev/sdd1 en media/ssd1


Lo que no entiendo es que si tengo permisos de root y estoy en el grupo de root no lo monta automáticamente.

Descubrí que el problema lo tengo solo sobre el ssd1, si conecto 2 pendrives, con el segundo no tengo problemas.

Ayuda!!!

---

### Post by KaKuS on 2009-01-28
Bueno lo resolví, no se porque y no se como pero en el FSTAB, en la línea de SSD estaban agregados unos parámetros con opciones que no eran las propias de un Pendrive.

Edite la línea y ahora funciona todo bien....

Podríamos decir CASO CERRADO (?)

---

