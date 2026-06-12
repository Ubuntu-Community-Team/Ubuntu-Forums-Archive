---
title: "how to create a swap partition (logical) after installation ?"
date: 2008-08-24
forum: General Help
---

### Post by jicarre on 2008-08-24
Hi,



Could you tell me how to create a swap partition after I installed already four primary partitions ? I dit that partioning with Gparted but I have no right to build a fith one.  :(

---

### Post by sandysandy on 2008-08-24
u will have to delete one primary partition and make a new extended partition as only max of 4 primary partitions are allowed.

in this new extended partition u can make multiple logical partitions.

post output of [COLOR="Blue"]sudo fdisk -lu
[/COLOR]
regards

---

### Post by jicarre on 2008-08-24
Thanks SANDY,

I am working on it ! I will tell you if I succeed to do it.

New question regarding SWAP. Is SWAP necessary for using some programs like simple backup or another one ?
Because I noticed it was not possible to proceed restore backup file. It is saying DUMMY and I do not have SWAP partition because of the crash of my computer and recovery an old temp  /home.

That is the reason, I am working on it: In order to verify...:confused: :confused:

---

### Post by jicarre on 2008-08-24
Sorry,I had just forgot to post the result :




Disque /dev/sda: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x00000010

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1              63   126977759    63488848+   7  HPFS/NTFS
/dev/sda2       126977760   338762654   105892447+   7  HPFS/NTFS
/dev/sda3   *   338762655   389495924    25366635   83  Linux
/dev/sda4       389495925   488392064    49448070   83  Linux

Disque /dev/sdb: 500.1 Go, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x0001e359

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1   *        2048   109932543    54965248    7  HPFS/NTFS
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sdb2       109932795   238019039    64043122+   7  HPFS/NTFS
/dev/sdb3       238019040   764003204   262992082+   7  HPFS/NTFS
/dev/sdb4       764003205   976768064   106382430   83  Linux

Disque /dev/sdc: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x783e4105

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1              63   125997794    62998866   83  Linux
/dev/sdc2       125997795   336192254   105097230    7  HPFS/NTFS
/dev/sdc3   *   336192255   381238514    22523130   83  Linux
/dev/sdc4       381238515   488392064    53576775    5  Extended
/dev/sdc5       381238578   476696744    47729083+  83  Linux
/dev/sdc6       476696808   488392064     5847628+  82  Linux swap / Solaris
jicarre@jicarre-desktop:~$ 

Sorry for the big mess !
TWo hard drive and one more in external

---

### Post by sandysandy on 2008-08-24
> **jicarre said:**
> Thanks SANDY,

I am working on it ! I will tell you if I succeed to do it.

New question regarding SWAP. Is SWAP necessary for using some programs like simple backup or another one ?
Because I noticed it was not possible to proceed restore backup file. It is saying DUMMY and I do not have SWAP partition because of the crash of my computer and recovery an old temp  /home.

That is the reason, I am working on it: In order to verify...:confused: :confused:

if u have enough memory (RAM) SWAP may not be really required for most tasks, unless u hibernate.

for info on [COLOR="Red"]SWAP[/COLOR] files go thru these links

[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/)

for more info on [COLOR="Red"]primary partitions[/COLOR] see these

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

for gparted tutorial on [COLOR="Red"]modifying partitions[/COLOR] see this

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

if u like u can post a snapshot of the drive on which u want to modify partitions (using gparted).

regards

---

### Post by mahuyar on 2008-08-24
Swapfile can also be a file instead of a partition.  Follow this [tutorial]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html") from Red Hat.  The second part of that tutorial tells you how to create a swap file and how to make it active.

---

### Post by jicarre on 2008-08-26
Thank you for all your information,


I did it, that is OK now!


I did it with Gparted... And I removed a partition to build a new one in "extended" ... So it allows to buid in a logic partition inside the extended.

I am very happy for your help and many thanks !):P

---

