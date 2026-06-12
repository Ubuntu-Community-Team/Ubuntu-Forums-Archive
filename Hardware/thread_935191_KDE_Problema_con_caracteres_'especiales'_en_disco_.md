---
title: "KDE: Problema con caracteres 'especiales' en disco USB NTFS"
date: 2008-10-01
forum: Hardware
---

### Post by gurlinux on 2008-10-01
Hola gente,

Soy bastante nuevo en Linux, tratando de migrar a Kubuntu. A ver si alguien me puede ayudar... 

Hay un problemita que no me deja avanzar: tengo un disco externo USB, formateado en NTFS (ya que lo comparto con maquinas WinXP). Kubuntu lo autodetecta bien, lo monta solo y hasta puedo escribir (read/write permission) al toque.
PERO no me deja escribir o crear ningun archivo que en el nombre contenga un caracter 'especial' como letras con acentos.

Investigue por todos lados, encontre que KDE tiene un problema con esto ([http://wiki.archlinux.org/index.php/HAL#Locale_issues](http://wiki.archlinux.org/index.php/HAL#Locale_issues)) y para verificar instale Gnome, por lo que ahora transforme Kubuntu en Ubuntu, y anda bien.

Las 'soluciones' que encontre a este problema de KDE en forums no funcionaron, mas bien casi me dejan la PC dada vuelta, asi que ya no se como hacer. Pero pude saber que esta montando con la codification de caracteres erronea: deberia ser UTF-8.

Ya puse un post en el forum general en ingles ([http://ubuntuforums.org/showthread.php?t=909806](http://ubuntuforums.org/showthread.php?t=909806)), pero no obtuve nada (parece que a los gringos los caracteres 'raros' como los acentos no les interesa demasiado).

A alguien que usa castellano le tiene que haber pasado lo mismo... Cualquier ayuda sera MUY agradecida!!

---

### Post by marianom on 2008-10-01
Tenemos un par de fanas de KDE en el foro que seguro te pueden dar una mano. Voy a ver si puedo editar tu post original y poner la palabra KDE en el título para que les llame la atención.

---

### Post by sergiom99 on 2008-10-01
a mi me pasa algo parecido descomprimiendo rar que baje en el emule y contienen archivos con caracteres especiales en el nombre.
(es un bajon tener que cambiar uno por uno los nombres de las canciones de 5 discos!!)
no he podido encontrarle la vuelta tampoco.

---

### Post by faktorqm on 2008-10-01
No importa el entorno de escritorio, el problema esta en como montas en pendrive. postea por favor "sudo fdisk -l". salu2!

sergio: postea tu /etc/fstab a ver como estas montando las cosas. salu2!

---

### Post by sergiom99 on 2008-10-01
faktor: aca lo dejo.
Lo habiamos visto en este otro thread, pero desde ahi que sigue igual:
[http://ubuntuforums.org/showthread.php?t=874452&highlight=rar+caracteres+fstab](http://ubuntuforums.org/showthread.php?t=874452&highlight=rar+caracteres+fstab)
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=68124ed6-880b-403b-bbf6-2aa534971b79 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c3aa61e4-b3ea-418a-b4bb-d73ca1e50b02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by gurlinux on 2008-10-02
Gracias a todos por responder! Esta visto que no soy el unico con este dilema.

> **faktorqm said:**
> No importa el entorno de escritorio, el problema esta en como montas en pendrive. postea por favor "sudo fdisk -l". salu2!


faktorqm: te aseguro que el problema sucede con KDE, no con Gnome, por raro que parezca. Esta comprobado y es un bug confirmado oficialmente ((en los links de arriba estan esos datos).
En cuanto a como se monta el disco, yo no lo hago ya que es totalmente automatico. Igualmente aca esta el "sudo fdisk -l" (solo la porcion correspondiente al disco USB extraible en cuestion):

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47d8e609

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdf5               2       60801   488375968+   7  HPFS/NTFS

Gracias!

---

### Post by faktorqm on 2008-10-03
Serg: La verdad estoy un poco desconcertado yo tambien, podrias probar de crear la carpeta "usb" en /media (con mkdir) y luego poner

```
sudo mount -t vfat,iocharset=utf8 -o defaults,user,utf8,umask=007,gid=46 /dev/sdb1 /media/usb
```

a ver que pasa, con respecto al rar, tiene caracteres que vos veas mal en el nombre del rar? por ejemplo, discos.rar estaria bien xD
usas unrar free pero privativo o el unrar libre? por que hay dos, en una de esas le embocas con alguno de los dos.

Sino podrias hacer como dice aca directamente desde el fstab (acordate de poner sdb1) [http://www.tuxapuntes.com/tux/content/view/19/141/](http://www.tuxapuntes.com/tux/content/view/19/141/)

gurlinux: capo no veo todas tus particiones ahi... donde esta el KDE? salu2!

---

### Post by gurlinux on 2008-10-05
> **faktorqm said:**
> gurlinux: capo no veo todas tus particiones ahi... donde esta el KDE? salu2!

faktorqm: no se muy bien para que te hace falta el resto, pero ahi va todo completo:

```

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17544   140922148+   7  HPFS/NTFS
/dev/sda2           17545       35376   143235540    f  W95 Ext'd (LBA)
/dev/sda3           35377       36481     8875912+   c  W95 FAT32 (LBA)
/dev/sda5           17545       34648   137387848+  83  Linux
/dev/sda6           34649       35376     5847628+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47d8e609

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS

```

Como veras, el disco del que hablo es el segundo. Gracias

---

### Post by Hei Ku on 2008-10-05
Ojo que KDE monta esa clase de dispositivos usando FUSE, asi que no aparecen en el fstab.

---

### Post by faktorqm on 2008-10-06
ajam... y entonces? jajaj

proba ```
cd /media
```
```
sudo mkdir pendrive
```
```
sudo mount -t vfat,iocharset=utf8 -o defaults,user,utf8,umask=007,gid=46 /dev/sdc1 /media/pendrive
```

a "pendrive" si queres lo podes cambiar por el que mas te guste. Te pedi el listado de particiones no por que soy espia de cia ni nada por el estilo, pero el pendrive lo toma con la letra siguiente desde la ultima particion, en tu caso la c (por eso es sdc) y la unica manera que tengo de saber es eso es pidiendote el listado de particiones.

fijate si te anda con eso, la verdad la unica vez que me pelie con fuse hice lo que decia un how to pero ni idea. Cualquier cosa lo vemos si no te funciona. Salu2!!

---

