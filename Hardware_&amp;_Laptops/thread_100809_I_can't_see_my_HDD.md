---
title: "I can't see my HDD"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by anarchist_hippy on 2005-12-08
My computer is;
AMD 3000+ 64 Bit CPU
1024 DDR 400 Ram
Asus K8N Mainboard
Asus FX5200 Graphic Card
200 GB Sata HDD

When I use windows, my HDD was 3 part. When I install ubuntu seperate c part 2, then install ubuntu into one of them. When the installation is done, ubuntu started. But I can't see my other parts of my hdd. I can only see the partition that Ubunto install into... 

What should I do?! 

PS: It's my first linux installation...

---

### Post by towsonu2003 on 2005-12-08
can you post the output of these ```
sudo fdisk -l
cat /etc/fstab 
```

---

### Post by tonysathre on 2005-12-08
the problem is that ubuntu by default cant read ntfs formatted partitions, to read them see this: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)
this will allow u to read your ntfs partition but write to it, and it will automount at boot

---

### Post by anarchist_hippy on 2005-12-08
[QUOTE=towsonu2003]can you post the output of these ```
sudo fdisk -l
cat /etc/fstab 
```[/QUOTE]

Here is the outputs;

root@anarchy:/home/anarchy # sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bayt
255 kafa, 63 sektör/iz, 24321 silindir
Birimler = silindir / 16065 * 512 = 8225280 bayt

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sda1               1        3648    29302528+  83  Linux
/dev/sda2            3649       16708   104904450    f  W95 Ext'd (LBA)
/dev/sda3           16709       24321    61151422+   7  HPFS/NTFS
/dev/sda5            7650       16708    72766386    7  HPFS/NTFS
/dev/sda6            3649        7649    32137969+  83  Linux


root@anarchy:/home/anarchy # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
root@anarchy:/home/anarchy #

PS: Language is turkish

---

### Post by anarchist_hippy on 2005-12-08
I do both of your advices... But nothing changed... :( :confused:

---

### Post by anarchist_hippy on 2005-12-08
I solve the problem from that page [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Thanx everyone...

---

### Post by towsonu2003 on 2005-12-08
For language-Turkish, there is also a turkish forum for ubuntu at [http://ubuntu-tr.com/forum.php](http://ubuntu-tr.com/forum.php) (I'm turkish). 

My advice was more about investigating.. 
Your setup doesn't seem to have a swap partition. swap is recommended in all linux systems. 
From your post, I'm assuming you mounted the following 3 partitions successfully:
/dev/sda2 W95 Ext'd (LBA)
/dev/sda3 HPFS/NTFS
/dev/sda5 HPFS/NTFS

Have fun with your linux :)

---

### Post by anarchist_hippy on 2005-12-08
[QUOTE=towsonu2003]For language-Turkish, there is also a turkish forum for ubuntu at [http://ubuntu-tr.com/forum.php](http://ubuntu-tr.com/forum.php) (I'm turkish). 

[/QUOTE]

:cool:  thanks...

---

