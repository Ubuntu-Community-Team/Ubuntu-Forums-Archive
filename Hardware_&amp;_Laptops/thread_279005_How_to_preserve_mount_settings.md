---
title: "How to preserve mount settings?"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by driggins on 2006-10-17
Greetings,

I am working with two device partitions: hdd1 and sda1. After boot-up, Ubuntu does not mount hdd1 at all. It does mount sda1, but not where I want it.

I am using Disks Manager to establish and change mount points for these partitions. After I set them up the way I want them, they work fine. When I reboot, these settings disappear and the partitions revert to their former status (hdd1 unmounted and sda1 mounted to the wrong folder).

Thoughts?

Thanks,
daryl

---

### Post by adwait on 2006-10-17
Change the settings in /etc/fstab....not quite sure about the GUI way to do this.

---

### Post by driggins on 2006-10-17
Hmm. It seems the GUI application is not saving my mount info.

Here is my current fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Both hdd1 and sda1 have ext3 file types. It looks like I can add the following to fstab and achieve automatic mounting:
> /dev/hdd1       /media/data               ext3    defaults,errors=remount-ro 0       
/dev/sda1       /media/backup               ext3    defaults,errors=remount-ro 0

I am just copying the settings for hda1 and modifying the mount point. Should this do the trick?

Thanks,
daryl

---

### Post by adwait on 2006-10-17
Yes I think it should, but by default they'll be owned by root so if you want someone else to own these drives, you need to specify.

---

### Post by CeeDub on 2006-10-17
How do you specify read/write priveledges?

---

### Post by driggins on 2006-10-17
CeeDub,

I don't have the syntax, but lookup info on "chmod" (e.g. try "man chmod" in a terminal window).

In my case, the partition I am sharing houses our office's shared data, so I have made it readable and writable for everyone. The equivalent chmod is "777".

Hope that gets you started.

---

### Post by adwait on 2006-10-17
Try
```
man fstab
```

It will tell you everything you need to know about fstab.

---

