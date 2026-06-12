---
title: "Problem whth USB Drive"
date: 2005-01-10
forum: Hardware &amp; Laptops
---

### Post by tino on 2005-01-10
I have a 60 GB external USB hard drive (fat32 formated).
It works perfectly under Windows XP. I also tested it with Drive Fitness. 
Under Ubuntu I can mount it and I can open files edit and save.
But if I want to copy or paste files to the drive I get the error:
»E/A-Fehler« beim Kopieren von »/home/tino/tuxbliss.png«.
After that I can not use the drive until I unplug the drive and plug it again.

Here my /etc/fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

And the commando dmseg: 

tino@ubuntu:~ $ dmesg
ad(block 28659) failed
scsi0 (0:0): rejecting I/O to dead device
FAT: Directory bread(block 28660) failed
scsi0 (0:0): rejecting I/O to dead device
...
FAT: Directory bread(block 28703) failed
scsi0 (0:0): rejecting I/O to dead device
FAT: unable to read inode block for updating (i_pos 458251)

I have no idea what the problem is  :-(  

I hope somebody can help me.

Best,

tino

---

