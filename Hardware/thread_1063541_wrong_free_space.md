---
title: "wrong free space"
date: 2009-02-08
forum: Hardware
---

### Post by Luiggipro on 2009-02-08
hi, I got a new pc, with a 250 gb sata hard drive. I installed ubuntu 32 bit but it shows wrong free space in my hard drive, it is like "eating" 20 gb. :(

---

### Post by taurus on 2009-02-08
What are the output of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
free -m
df -h
```

---

### Post by Vaphell on 2009-02-08
2 possible things:
- manufacturers use GB = 10^9B while often OS counts GB as 2^30 - it's not the same and hdd appears bigger in manufacturer's way of counting
- ubuntu reserves ~5% of hdd space - total space and free+used space don't match (to allow root to log in in case of fixing things, full hdd would prevent that), you can change that number to anything, even to 0%

---

### Post by Luiggipro on 2009-02-09
ok:
luiggi@luiggi-desktop:~$ sudo fdisk -l
[sudo] password for luiggi: 

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000bf33a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       29741   238894551   83  Linux
/dev/sda2           29742       30401     5301450    5  Extendida
/dev/sda5           29742       30401     5301418+  82  Linux swap / Solaris

luiggi@luiggi-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cbef4188-2fcc-4696-8d83-150b706997e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=074dbf14-b875-407a-8e2f-354f8897d2f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


luiggi@luiggi-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1515        880        634          0         22        530
-/+ buffers/cache:        327       1188
Swap:         5177          5       5171


luiggi@luiggi-desktop:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda1             225G   34G  180G  16% /
tmpfs                 758M     0  758M   0% /lib/init/rw
varrun                758M  300K  758M   1% /var/run
varlock               758M     0  758M   0% /var/lock
udev                  758M  2.8M  756M   1% /dev
tmpfs                 758M   12K  758M   1% /dev/shm
lrm                   758M  2.0M  756M   1% /lib/modules/2.6.27-11-generic/volatile

---

### Post by Luiggipro on 2009-02-11
bump :(

---

### Post by Luiggipro on 2009-03-06
bump .. :(
Its "eating" space from usb storage devices too. (4 gb stick indicating 3.6 gb)

---

