---
title: "Problema para particionar disco externo"
date: 2010-07-24
forum: Hardware
---

### Post by donmatas on 2010-07-24
Estimad@s:

tengo un HD 500Gb de Toshiba. El problema es que funciona más lento que tortuga cruzando Los Andes, así que estoy decidido a pasarlo en un 90% a Ext4 (supongo que eso mejorará su rendimiento). El problema es que al abrir gparted y seleccionar el disco externo éste parece con un signo de exclamación y una llave y no me da opciones de partición. Al intentar desmontarlo no pasa nada y si lo pincho me sale la info del disco con el siguiente mensaje:
```
Imposible encontrar el punto de montaje
Imposible leer el contenido de este sistema de archivos
Debido a esto, algunas operaciones pueden no estar disponibles
```

alguna sugerencia?

gracias
DM

---

### Post by donmatas on 2010-07-24
Más info sobre mi problema:
```

$ sudo fdisk -l
[sudo] password for matas: 

Disco /dev/sda: 58.5 GB, 58506416640 bytes
255 cabezas, 63 sectores/pista, 7113 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xcfce28df

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5140    41287018+   7  HPFS/NTFS
/dev/sda2            5141        5763     5004247+  83  Linux
/dev/sda3            5764        5887      996030   82  Linux swap / Solaris
/dev/sda4            5888        7113     9847845   83  Linux

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xc27c4f8f

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       60801   488383008+   c  W95 FAT32 (LBA)
matas@el-anarquista:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda2 :
UUID=34f6dfc2-2b09-476b-b87a-e0b2acd64ba3	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=4778e962-8045-4294-bbdd-710c2e3e154e	/home	ext4	defaults	02
#Entry for /dev/sda1 :
UUID=783CF0F23CF0ABEE	/media/XP	ntfs-3g	defaults,locale=es_CL.UTF-8	00
#Entry for /dev/sda3 :
UUID=de239cca-d464-41d9-acd6-c25bd44e6da0	none	swap	sw	0	0

```

---

