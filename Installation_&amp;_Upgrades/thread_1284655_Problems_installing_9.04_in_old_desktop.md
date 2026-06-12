---
title: "Problems installing 9.04 in old desktop"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by pedro.amaro on 2009-10-06
I am running a Windows XP on a Hewlett Packard. The settings of my system are as follows:

1.9 ghz intel processor, 
512MB of memory 
and a  120GB Hard Drive

When I try to intall the program and get to the point where it asks where do I want to put it I select use the entire hard drive. I get to step number 7 and once it starts installing the program it sends me back tostep number 4 which is the partition part.

I have only been able to get to 15% of the installation process when the following error comes up:

The ext3 file system creation in partition # 1 of SCSI1 (0,0,0) (SDA) failed.

Can anyone help me with this?

---

### Post by stlsaint on 2009-10-06
have you done any diagnostics on the hdd? there are some things you can check like the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM"). but this sounds like a bad hdd.

---

### Post by rreese6 on 2009-10-06
try:
boot liveCD
open Terminal
make sure /dev/sda is unmounted.  then run fdisk
```
sudo umount /dev/sda
sudo fdisk /dev/sda
```

Press "m" for menu.
Press "p" to list partitions currently on drive.
whatever you see delete the partitions.
write and quit fdisk
close termnal.
try install again.

---

