---
title: "The Dodgy DVD-ROM drive"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by insane_alien on 2007-06-15
okay, i've been trying to fix this problem for a long time now.
My DVD-ROM drive won't open if you push the button or use the eject command.

well, it usually doesn't

the only situation where it will open when the button is pressed is immediately after the power is switched on. by the time it gets to GRUB it'll be stuck again. anyone have a clue what causes this and how to fix it?

---

### Post by DagMan on 2007-06-15
What happens if you type 
sudo umount /dev/cdrom
and then hit the eject button?  Is it still not releasing it?

If that does work btw, I don't know how to fix it so that the button unmounts and ejects so someone else will have to pick it up from there.

---

### Post by insane_alien on 2007-06-16
nope. nada.

it opens fine if you only connect it to the power supply. but thats it.

if you put a DVD i nthrough the use of a paper clip then it'll read it and play it fine just won't let you get it back out without a paper clip.

---

### Post by ajmorris on 2007-06-17
can you post your /etc/fstab file please.

---

### Post by neptho on 2007-06-17
Try this:

```
sudo sysctl dev.cdrom.lock=0
```

If it works, to make it remember over boots:

```
sudo &#8216;echo dev.cdrom.lock=0 >> /etc/sysctl.conf
```

---

### Post by insane_alien on 2007-06-17
i'll post the results of these tomorrow. i'm not at my house today.

---

### Post by insane_alien on 2007-06-18
/etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=815ba332-abc5-4c96-8e8c-698f1c705045 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=74385e9c-d922-46dc-8dd2-d6e4198493c8 /home           ext3    defaults        0       2
# /dev/sda5
UUID=fc86edb2-66dd-4be9-9439-6f3a86067e9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

the sysctl command doesn't work. possibly because i have to DVD drives hooked up?

---

### Post by insane_alien on 2007-06-21
bump?

---

