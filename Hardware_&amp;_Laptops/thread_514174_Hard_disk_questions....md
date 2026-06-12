---
title: "Hard disk questions..."
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by NobleSavage on 2007-07-31
I just installed Feisty on a computer that has 2 IDE drives.  I previously had LTS on this computer. I created the partitions with fdisk on a Knoppix live cd and then I used the alternative install disk for Feisty.

The disks show up as /dev/sda and /dev/sdb  ???   Shouldn't they be /dev/hda and /dev/hdb ???

This is my /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4aa5eadb-d88e-405f-8297-b757e87f9ca4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=ada45120-9836-46af-9ffc-408a1e4a8d41 /boot           ext3    defaults        0       2
# /dev/sda5
UUID=f522670d-1e2a-4fa1-b9d1-78afa64bcd07 /home           ext3    defaults        0       2
# /dev/sdb6
UUID=eb2f2e4a-db21-4536-b5bd-e48c2ce37d72 /media/sdb6     ext3    defaults        0       2
# /dev/sda1
UUID=deffc17c-12b3-44d5-9503-3aa56fd73895 none            swap    sw              0       0
# /dev/sdb5
UUID=2c840450-084f-17b8-43c6-9c06105f034f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
noble@Zeus:~$

---

### Post by merlinus on 2007-07-31
No. sda and sdb are correct for Feisty.

-merlin

---

### Post by NobleSavage on 2007-07-31
Why the change?   /dev/sdb6   auto mounted to a icon on my desktop.   When I try to unmount it I get

 umount: /dev/sdb6 mount disagrees with the fstab

Any reason it won't unmount?

Thanks

---

### Post by merlinus on 2007-07-31
You need to use sudo to unmount drives.  For example:

```

sudo umount /dev/sdb6

```-merlin

---

### Post by NobleSavage on 2007-07-31
Thanks -merlin,

Now when I mount it where I want it  I keep getting an icon on my desktop.   How do keep that from happening?

---

### Post by merlinus on 2007-07-31
Alt-F2
gconf-editor
apps/Nautilus/desktop

Untick appropriate boxes.

-merlin

---

