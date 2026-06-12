---
title: "I have a problem with my cd-rom"
date: 2005-11-10
forum: General Help
---

### Post by Humble on 2005-11-10
I have a plextor serial-ata DVD-rom. The problem is that when I insert a cd nothing happens and when I try manually mount the device it says "mount: special device /dev/scd0 does not exist". My fstab looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Can someone tell me what I should do to correct this problem?

---

### Post by az on 2005-11-10
Have you tried mounting /dev/scd1?

sudo mount /dev/scd1 /mnt

Have you changed or added any hardware?

---

### Post by Humble on 2005-11-10
I haven't changed any hardware since my install. I tried to mount it like you said, but it asks me to specify the filesystem type... how do I do that?

---

### Post by Humble on 2005-11-11
Last night I checkde my /dev folder and found no scd0 or anything reminding a cd drive...

How can I ad a cd drive or make sure it isn't named someway really wierd?

---

### Post by hackyou on 2006-02-27
Same problem here... Did somebody find a way to make the cdrom work again?

Cheers

---

### Post by Ramses de Norre on 2006-02-27
To specify the file system type sudo mount -t iso9660 /dev/scd1 /media
Don't know whether it will work though..

---

### Post by Bionic_Beefpile on 2006-06-12
I'm having the same problem.  I've posted a bit about it over in this thread:
[http://ubuntuforums.org/showthread.php?p=1130026#post1130026](http://ubuntuforums.org/showthread.php?p=1130026#post1130026)

So far, no help :(

---

### Post by Bionic_Beefpile on 2006-06-13
I think I got it fixed.  See the thread I linked in the previous post

---

