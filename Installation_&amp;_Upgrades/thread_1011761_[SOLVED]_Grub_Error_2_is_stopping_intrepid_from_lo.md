---
title: "[SOLVED] Grub Error 2 is stopping intrepid from loading"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-12-15
I am having a grub error 2 on start up of my reinstalled system.

Previously I had been running 8.10 but there were sound problems and other minor faults.  I decided to reformat the root and install a fresh version of Intrepid. 

My root directory is sdb1 and the home sdb2. I set these  up on the manual installation. I only reformatted sdb1.

Because of the grub error I can not run Ubuntu any more.
 

Advice as to correction would be very appreciated



```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    59842124    29921031   83  Linux
/dev/sdb2        59842125   122849054    31503465   83  Linux
/dev/sdb3       122849055   964815704   420983325    5  Extended
/dev/sdb4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sdb5       122849118   205358894    41254888+  83  Linux
/dev/sdb6       205358958   410412554   102526798+  83  Linux
/dev/sdb7       410412618   964815704   277201543+  83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo cp /usr/lib/grub/i386-pc/* /mnt/boot/grub
cp: target `/mnt/boot/grub' is not a directory

```

In another thread this information was also requested:

sudo xxd  -l  2 -p /dev/sda
eb48

ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0081

ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda1
5152


ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sdb
eb48
ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sdb1
0000
ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sdb2
0000

---

### Post by Robbyx on 2008-12-15
Could someone please help me out of this hole and answer my query.

I am without an effective computer as I am having to run off the live cd.

I have tried to install supergrub onto a usb drive. It is not being recognised on startup. I have changed the bios boot options to what  I think relate to the usb drive but that has made no difference.

---

### Post by Robbyx on 2008-12-15
I am still not clear exactly how I repaired the system but in essence I used supergrub.

---

