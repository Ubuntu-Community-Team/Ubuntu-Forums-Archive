---
title: "&quot;Not enough space ... updated.&quot; Help!"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Starkill on 2009-11-06
Hello! My problem is that when trying to update (update manager) tells me I do not have enough space in the directory "/".  This happens some time with the updates and now with the new version of Ubuntu, but had almost 10 Gb for the root partition.  Neither the "janitor" or the command "sudo apt-get clean" useless.

---

### Post by pastalavista on 2009-11-06
Try booting in recovery mode and run fsck (file system check) and reboot.

If it doesn't help, post the output from terminal (Applications-> Accessories-> Terminal) ```
sudo fdisk -l
```

---

### Post by Starkill on 2009-11-09
Thank you very much for your reply. I did what I recommend without problems, but the problem persists. I could upgrade my current release of Ubuntu , but the "Update Manager" keeps saying there is not enough space in "/" when I want to upgrade to 9.10 the distribution verision.  I'm quite a rookie, and I'm scared s more drastic solutions...  Should I start uninstall everything? Â Can you format without losing all the information in the hard drive?

---

### Post by pastalavista on 2009-11-09
What I asked you to do was post the output of the command. It won't fix anything. It might help show what is wrong though.

---

### Post by Starkill on 2009-11-10
My English is really bad, apologies. What you say is true, is like a poetry-a.  This is information that gives the command you gave me:


starkill@ATHEA:~$ sudo fdisk -l
[sudo] password for starkill:

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x10341033

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1075     8634906   83  Linux
/dev/sda2            1338       30401   233456580    f  W95 Ext'd (LBA)
/dev/sda3            1076        1337     2104515   82  Linux swap / Solaris
/dev/sda5            1338       30401   233456548+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1813 MB, 1813381120 bytes
241 cabezas, 32 sectores/pista, 459 cilindros
Unidades = cilindros de 7712 * 512 = 3948544 bytes
Identificador de disco: 0xc3072e18

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         513     1975664    b  W95 FAT32
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(249, 240, 32) lógicos=(512, 87, 32)
starkill@ATHEA:~$


Regarding the poetry, I'm half illiterate, so I think I have a long way to achieve understanding. I'm spelling in the informatic world.  ;)

---

### Post by Rahsaan on 2009-11-10
I am 2 weeks new to Ubuntu and also am limited to 10.1 gb free according to properties. I think over 100 gb should be free. I thank you in advance.

 tadnin@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f4d5e28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19458   154752000    7  HPFS/NTFS

Disk /dev/mmcblk0: 7950 MB, 7950303232 bytes
146 heads, 11 sectors/track, 9668 cylinders
Units = cylinders of 1606 * 512 = 822272 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               6        9669     7759872    b  W95 FAT32

---

### Post by Starkill on 2009-11-11
Sorry, I do not understand what you mean ...

---

