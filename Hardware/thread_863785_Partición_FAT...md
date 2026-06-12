---
title: "Partición FAT.."
date: 2008-07-18
forum: Hardware
---

### Post by [P]oli on 2008-07-18
Gentee, acá les presento una gran cuestión con una partición FAT:
Tengo mi HD de 80GB dividido en:
10GB para Ubuntu HH, 
1GB para SWAP
y lo que resta (aprox 68-69GB) para una partición FAT, en donde dejo todos los datos importantes, mp3's, etc etc.

Lo que me viene pasando, es que cuando quiero eliminar algún archivo de esa partición, me dice 
```

No se puede mover el archivo a la papelera, ¿Desea borrarlo inmediatamente?
El archivo <<...>> no se puede mover a la papelera

```

Tampoco deja a algunos programas (instaladores que emulo con WINE) escribir en la partición. Por eso empecé a buscar, y encontré algunas opciones que supuestamente al modificar fstab me iban a dejar con todos los permisos, pero no. Posteo mi fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0a2c2b7e-c3ac-48c3-b8e5-a202cea0af48 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=5be96cb3-3dec-44bb-a15e-90cb4adb3f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3	/media/hda3	vfat	rw,users,auto,umask=000,utf8	0	0

```

Help please! :confused: :D

---

### Post by faktorqm on 2008-07-19
1) No es una partición FAT, es FAT32.
2) En una partición FAT ó FAT32 no se dejan los datos importantes. Se dejan en EXT3 o XFS.
3) WINE = Wine Is Not an Emulator (Wine no es un emulador)

Podrias probar en cabiar la linea del fstab por esto a ver que pasa:

```
/dev/sda3	/media/hda3	vfat	rw,users,auto,umask=777,utf8	0	0
```

Salu2!

---

### Post by [P]oli on 2008-07-19
> **faktorqm said:**
> 1) No es una partición FAT, es FAT32.
2) En una partición FAT ó FAT32 no se dejan los datos importantes. Se dejan en EXT3 o XFS.
3) WINE = Wine Is Not an Emulator (Wine no es un emulador)

Podrias probar en cabiar la linea del fstab por esto a ver que pasa:

```
/dev/sda3	/media/hda3	vfat	rw,users,auto,umask=777,utf8	0	0
```

Salu2!


1) Es un detalle al que no le doy mucha importancia (ya se que debería darselo)
2) No entiendo por qué, 
3) Si no es un emulador qué es?

```
Gracias, pero sigue haciendo lo mismo,
```

Slds!

---

### Post by Mauro22 on 2008-07-19
3) Wine tiene las API's de Windows, logrando correr programas que las necesitan. No emula ni mucho menos, sino que le da a los programas las apis que necesitan para ejecutarse.

Yo lo tengo asi:

```
/dev/sda4       /media/datos    vfat iocharset=utf8,umask=000 0 0
```


No se si es importante pero desmonta el disco, modifica el fstab y montalo de nuevo



Suerte

---

### Post by Hei Ku on 2008-07-19
FAT32 es un sistema de archivos que tiene varios problemas. Los principales son la fragmentación, lentitud y la poca confiabilidad y poca capacidad de recuperación ante errores. Además que no soporta nativamente nombres largos y entonces tiene hecho un emparche que anda más o menos, y cuando quiere.
Salvo que estés compartiendo datos con una instalación de Windows, es altamente recomendable que cambies la partición a EXT3. Obviamente si sólo tenés ese disco no es algo fácil de hacer, pero para la próxima, te conviene pasar a EXT3, EXT4, reiserFS, etc. Hasta a NTFS, si te place, aunque no te lo recomiendo. ;)

Y otra cosa, yo tuve problemas en su momento ejecutando archivos cuando estaban en la partición FAT32. Terminaba pasándolos a la EXT3 para correrlos.

---

### Post by [P]oli on 2008-07-20
> **Mauro22 said:**
> 3) Wine tiene las API's de Windows, logrando correr programas que las necesitan. No emula ni mucho menos, sino que le da a los programas las apis que necesitan para ejecutarse.

Yo lo tengo asi:

```
/dev/sda4       /media/datos    vfat iocharset=utf8,umask=000 0 0
```


No se si es importante pero desmonta el disco, modifica el fstab y montalo de nuevo



Suerte

Gracias a vos, y a Hei Ku, el próximo formateo (cuando instale Ubuntu II) hago la partición EXT3, por ahora me la banco así :P

**Gracias por contestar**,

---

### Post by pol666 on 2008-07-20
yo usaba fat32 y es un problema, por que es muy lenta para interactuar datos entre ubuntu, y la particion..


**Consejo:**
Lo que tendrias que hacer un dia, es esa particion convertirla en Ext3 y montarla en una instalacion como "/home" entoses ahi, pode sponer la musica, los programas, etc


Si tenes windows y queres entrar a la ext3 podes usar IFS que es un driver de particiones de linux para windows... Podes escribir y modificar con una buena velocidad, lo unico es tenes que reiniciar ubuntu correctamente por que si lo reinicias con el boton, despues el IFS no te anda (no se por que pero es asi)

---

### Post by [P]oli on 2008-07-20
> **pol666 said:**
> yo usaba fat32 y es un problema, por que es muy lenta para interactuar datos entre ubuntu, y la particion..


**Consejo:**
Lo que tendrias que hacer un dia, es esa particion convertirla en Ext3 y montarla en una instalacion como "/home" entoses ahi, pode sponer la musica, los programas, etc


Si tenes windows y queres entrar a la ext3 podes usar IFS que es un driver de particiones de linux para windows... Podes escribir y modificar con una buena velocidad, lo unico es tenes que reiniciar ubuntu correctamente por que si lo reinicias con el boton, despues el IFS no te anda (no se por que pero es asi)

Gracias, lo voy a tener en cuentaa (Y)

---

