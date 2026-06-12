---
title: "help mountig usb drive"
date: 2009-01-03
forum: Hardware
---

### Post by diegoallen on 2009-01-03
I need help mounting a pendrive, kubuntu does not do it automatically. As you can see below I attached the /var/log/messages output. If its any help Im running kubuntu X64. Mobo: Abit Ip35pro.



Jan  3 23:52:48 Diego-Kubuntu kernel: [10455.217403] sd 10:0:0:0: [sdc] 16580608 512-byte hardware sectors (8489 MB)
Jan  3 23:52:48 Diego-Kubuntu kernel: [10455.217904] sd 10:0:0:0: [sdc] Write Protect is off
Jan  3 23:52:48 Diego-Kubuntu kernel: [10455.217910]  sdc:
Jan  3 23:52:48 Diego-Kubuntu kernel: [10455.219290] sd 10:0:0:0: [sdc] Attached SCSI removable disk
Jan  3 23:52:48 Diego-Kubuntu kernel: [10455.219905] sd 10:0:0:0: Attached scsi generic sg3 type 0
Jan  4 00:18:50 Diego-Kubuntu -- MARK --
Jan  4 00:38:50 Diego-Kubuntu -- MARK --
Jan  4 00:58:50 Diego-Kubuntu -- MARK --
Jan  4 01:18:42 Diego-Kubuntu kernel: [15608.700660] usb 8-3: USB disconnect, address 4
Jan  4 01:38:50 Diego-Kubuntu -- MARK --

---

### Post by taurus on 2009-01-03
What about the output of 

```
sudo fdisk -l
```

---

### Post by Johnny-Cache on 2009-01-04
the sdg1 part might be different for your drive location but it will be located in the /dev directory.  

open a terminal:

fdisk -l

look for your pendrive . . . it will probably be called sdb or sdg

the make a mount point:
mkdir /pendrive

and mount the drive to your created location:

sudo mount /dev/sdg1 /pendrive -o force

hope that works, I had to play with the sdg1 part until I found where my usb drive is.

cheers

---

### Post by diegoallen on 2009-01-04
fdisk -l tells me that the pendrive is located at /dev/sdc.  I tryed to mount it on /media/pendrive, I used  ```
mount /dev/sdc /media/pendrive -o force
``` and ```
mount /dev/sdc /media/pendrive.
``` Both times got "mount: debe especificar el tipo de sistema de ficheros
" 
Debe especificar el tipo de sistema de ficheros=Spanish for must specify file system.

---

### Post by diegoallen on 2009-01-04
Also tried adding ```
#/dev/sdc
/dev/sdc    /media/pendrive   vfat   defaults,user,noauto   0  0
```
to /etc/fstab, and then mounting but didnt work either.

---

### Post by Johnny-Cache on 2009-01-05
I had the same message in Eng. . . I had to specify a location on the drive - it worked for me by adding a 1:

mount /dev/sdc1 /media/pendrive -o force

might also try:

sudo mount -t vfat /dev/sdc1 /media/pendrive -o force

---

### Post by diegoallen on 2009-01-05
solved my problem adding those code lines listed above in /etc/fstab. Some of it was spelled incorrectly the first time I did it so it didn't work.. Thanks to everyone anyway..

---

