---
title: "No arranca Ubuntu"
date: 2009-12-01
forum: Instalación y Actualización
---

### Post by jimdark on 2009-12-01
Les cuento
 
instale ubuntu hace un tiempo desde windows, con la utilidad wubi que viene en el mismo disco, el problema que tengo ahora, y gran problema ya que tengo un trabajo que debo entregar ahora, es que no me quiere arrancar el  sistema operativo. 
me tira el siguiente error.
 
Alert! dev/sdc5 does not exist.
 
entiendo que tiene que ver con la particion, o no?
necesito lo antes posible poder rescatar el archivo que tengo en este sistema, sino jodi.
 
alguna manera de arreglarlo o sacar el archivo desde windows o algun live cd mediante alguna linea de comando?
 
Hize un fdisk -l y aparecio esto, por si les sirve de ayuda.
```

ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0610bc20
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sda5               2      121601   976751968+   7  HPFS/NTFS
 
Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5d1c486
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   42  SFS
 
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00670067
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3928    31551628+   7  HPFS/NTFS
/dev/sdc2            3929       60801   456832372+   f  W95 Ext'd (LBA)
/dev/sdc5            3929       60801   456832341    7  HPFS/NTFS

```
 
espero sus respuestas.
 
sl2

---

### Post by moreback on 2009-12-02
¿Es idea mía o le pusiste otro disco a tu máquina? a lo mejor se corrieron las letras y por eso con /dev/sdb5 ya no te entra.

---

