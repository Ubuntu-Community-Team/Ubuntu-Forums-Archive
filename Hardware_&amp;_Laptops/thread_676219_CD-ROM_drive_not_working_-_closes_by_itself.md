---
title: "CD-ROM drive not working - closes by itself"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by jim0203 on 2008-01-23
I'm working on a student of mine's Ubuntu box and her CD-ROM is not working. While the drive is closed it seems to be permanently "seeking", like a CD has just been put in. The drive does open when I press the open/close button, but it closes, by itself, almost immediately.

In /media there is /cdrom0, so I tried to unmount it but I get the following message:

```

umount: /dev/cdrom0: not found

```

So, anyone got any ideas? The drive did work before; it might have stopped working when I upgraded to Feisty.

Thanks in advance,

--Jim

---

### Post by ajgreeny on 2008-01-23
There is always, and always should be a /media/cdrom0 showing, but it will not be mounted until there is a CD in the drive, then it will normally automount.  It is possible that your /etc/fstab file is not correct and that the entry for the cdrom crive is not quite as it should be.  Here is the line from my fstab
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```If yours is different, particularly in the various options (udf,iso9660 user,noauto,exec) that may be the reason.  I can't imagine why it should be wrong, but it's a possibility and worth checking.

---

### Post by jim0203 on 2008-01-23
Thanks for that - I will check this out, but as it's a student's machine I won't be able to do this until next week. I'll post back then. In the meantime, if anyone else wants to list other things I might try, I'd appreciate it.

---

### Post by jim0203 on 2008-02-08
OK, the fstab now looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=707a8c82-ce85-4082-9016-840e723cbfa7 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=500b3c0f-9b5a-423e-a527-6eb020cf807b none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto,exec     0       0

```

There was no "exec" in the cdrom line so I added that; I also tried changing /dev/cdrom to /dev/hda which is what yours was. But neither of these things worked.

What I find interesting is the commented lines which say "converted during upgrade to edgy" - I think it was after upgrading to Edgy that I started getting this problems.

Got any ideas how I solve this? Thanks for your help so far!

--Jim

---

