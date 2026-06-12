---
title: "VIA VT4610 kernel support"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2004-11-23
Hi,

I didn't get much reactions on : 

[http://www.ubuntuforums.org/showthread.php?t=4090](http://www.ubuntuforums.org/showthread.php?t=4090)

So I decided to change the topic name.

I want acces to my RAID array (It's full of data). My asus p4p800 deluxe motherboard has a VIA VT6410 RAID chip. I've got a raid array full of data (ntfs) I want to acces.

I think I need to recompile my kernel. But I don't know what options to set. I've found an howto with link to the via driver for 2.4 kernels. Maybe support is already in the 2.6-686 kernel ?

see also :

[http://www.ubuntuforums.org/showthread.php?t=4090](http://www.ubuntuforums.org/showthread.php?t=4090)

and :

[http://www.is.tu-braunschweig.de/~buethe/p4p800_raid.html](http://www.is.tu-braunschweig.de/~buethe/p4p800_raid.html)

---

### Post by jdong on 2004-11-23
sata_via drivers should have support for it.
 
 However, it probably wont' access your current raid.

---

### Post by ubuntu_demon on 2004-11-23
It's not SATA raid. It's PATA raid.

---

### Post by jdong on 2004-11-23
the ata_raid / ataraid module may support it, but most likely you're out of luck.

---

### Post by ubuntu_demon on 2004-11-23
do you mean modprobe or recompiling the kernel ?

sudo modprobe raid0
sudo mount /dev/sda1 /mnt/sda1 -t ntfs

gives :
mount: special device /dev/sda1 does not exist

---

### Post by ubuntu_demon on 2004-11-23
By the way it's a VT6410 chip (instead of VT4610)

---

### Post by ubuntu_demon on 2004-11-23
lsmod gives :

raid0                   8192  0
md                     48552  1 raid0

---

### Post by ubuntu_demon on 2004-11-24
Come on guys. Doesn't anyone know a solution for me ?

Is it possible to get raid working with the VIA VT6410 chip under linux kernel 2.6.x ? And how do I do it ?

is it possible to break my raid arry without losing my data ?

---

### Post by razzmatazz on 2005-01-31
Hey, use dmraid and device-mapper. It needs some tinkering, but is certainly possible to use half-software raid on 2.6.

I've successfully installed and I'm using ICH5-R RAID0 (stripe) as a bootable disk, with windows and ubuntu partitions.

---

### Post by ubuntu_demon on 2005-01-31
[QUOTE=razzmatazz]Hey, use dmraid and device-mapper. It needs some tinkering, but is certainly possible to use half-software raid on 2.6.

I've successfully installed and I'm using ICH5-R RAID0 (stripe) as a bootable disk, with windows and ubuntu partitions.[/QUOTE]
 thnx
I won't use it because I've decided to do things differently. (my p4 now only has 1 harddisk)

---

