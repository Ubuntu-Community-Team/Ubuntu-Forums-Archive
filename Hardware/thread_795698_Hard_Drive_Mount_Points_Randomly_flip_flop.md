---
title: "Hard Drive Mount Points Randomly flip flop?"
date: 2008-05-15
forum: Hardware
---

### Post by jrollf on 2008-05-15
I use my computer as a home file server, it has three drives:

sda = 30 GB IDE Ultra ATA33 WD, Primary Master on the motherboard (Ubuntu Boot Drive)
sdb = 500 GB SATA on a Syba SD-SATA-4P PCI SATA Controller (Port 1)
sdc = 500 GB SATA on a Syba SD-SATA-4P PCI SATA Controller (Port 2)

Every once in a while during boot up the drives swap places:

sda becomes sdb
sdb becomes sdc
sdc becomes sda

Usually a reboot fixes the problem.  What could be causing this.  It only happens once every 8 to 12 boot ups....

Thanks,
John

---

### Post by hermes0710 on 2008-05-16
I don't know what it might be causing this but i do know that if in your fstab you change your entries to point the uuids of the devices instead of the /dev/?? entries, everything will work smoothly.

To find your disks' uuids run:

```
ls /dev/disk/by-uuid -alh
```

Then manually edit your fstab entries and in the first columns of the according disks replace ```
/dev/???[code] with [code]UUID=THEUUID
``` where "THEUUID" is the uuid you got from the "ls" command above

PS>Post your current /etc/fstab file and the output of the "ls /dev/disk/by-uuid -alh" command for more help

---

### Post by jrollf on 2008-05-16
Thanks for the help!

Here is what I get with the ls command (with the drives mounted "correctly"):

59cc0880-c413-409a-afec-50587fcbbcfb -> ../../sda1
d83e2194-98c0-41c3-886e-a533b2fd9ec2 -> ../../sdb1
dd0cacb3-44ba-4bbc-905a-2d070907c9fe -> ../../sda5
f7c7e6b1-7634-4289-98ce-81574664a506 -> ../../sdc1

And below was my fstab before your suggested updates, note I only added the last two entries for sdb and sdc, everything else was done by Ubuntu when I installed it.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=59cc0880-c413-409a-afec-50587fcbbcfb /  ext3  relatime,errors=remount-ro 0 1

# /dev/sda5
UUID=dd0cacb3-44ba-4bbc-905a-2d070907c9fe none  swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb1
/dev/sdb1       /media/fs1      ext3    defaults        0        0

# /dev/sdc1
/dev/sdc1       /media/fs2      ext3    defaults        0        0


I noticed that the system already has sda1 and sda5 set up the way you suggested.  So how is sdc1 and sda1 swapping sometimes?  I've replaced the /dev/ds## with the UUID like you suggested, I guess time will tell if it works for me.

This is what I have using your suggestions:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=59cc0880-c413-409a-afec-50587fcbbcfb /  ext3 relatime,errors=remount-ro 0 1

# /dev/sda5
UUID=dd0cacb3-44ba-4bbc-905a-2d070907c9fe none  swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb1
UUID=d83e2194-98c0-41c3-886e-a533b2fd9ec2  /media/fs1 ext3  defaults    0      0

# /dev/sdc1
UUID=f7c7e6b1-7634-4289-98ce-81574664a506  /media/fs2 ext3  defaults    0      0


Thanks again!
John

---

