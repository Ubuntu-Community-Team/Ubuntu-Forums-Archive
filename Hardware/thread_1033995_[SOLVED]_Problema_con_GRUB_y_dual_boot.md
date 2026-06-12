---
title: "[SOLVED] Problema con GRUB y dual boot"
date: 2009-01-07
forum: Hardware
---

### Post by sergiom99 on 2009-01-07
Hola gente, convenci a mi hermano de instalar Ubuntu, pero lo arruine con el dual boot.
Al elegir el XP en el Grub me tira un "Error 22" no existe la particion o algo parecido.

En un disco de 500gb tiene XP y Ubuntu y tiene otro disco de 250Gb NTFS.

menu.lst (solo el final)
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
df -h
```
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sdb2             341G  2,9G  320G   1% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  100K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2,7M 1010M   1% /dev
tmpfs                1013M  104K 1012M   1% /dev/shm
lrm                  1013M  2,0M 1011M   1% /lib/modules/2.6.27-9-generic/volatile

```

fdisk -l
```

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00000001

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda2   *           2       30401   244188000    5  Extendida
/dev/sda5               2       30401   244187968+   7  HPFS/NTFS

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x799b799b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       15452   124118158+   7  HPFS/NTFS
/dev/sdb2   *       15453       60552   362265750   83  Linux
/dev/sdb3           60553       60801     2000092+   5  Extendida
/dev/sdb5           60553       60801     2000061   82  Linux swap / Solaris

```

dentro de grub:
```
grub> find /boot/grub/stage1
 (hd1,1)

```

busque mil threads pero no saque nada en concreto. Alguien me puede tirar una punta? 

Gracias!!
Sergio

---

### Post by sergiom99 on 2009-01-08
Probando editar la linea 
root		(hd1,0)

logre arreglarlo dejandolo en (0,0) => arranca de la primer particion del primer disco.

Auto-medalla para mi.

---

