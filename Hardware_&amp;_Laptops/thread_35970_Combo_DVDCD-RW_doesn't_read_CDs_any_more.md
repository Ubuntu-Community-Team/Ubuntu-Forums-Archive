---
title: "Combo DVD/CD-RW doesn't read CDs any more"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by tseliot on 2005-05-21
Today I've tried to install a dictionary from a CDR and it couldn't read it (it worked until last night). That is, it tried to read it and the CD light (of the reader) was on. I tried with my Kubuntu CD but nothing. It just doesn't work, it can't even mount it. Then I put on a DVD and it worked.

Now I'd like to know what I can do to see if it's just the laser of my reader that doesn't work (I had it changed last summer as it couldn't write cd any more, fortunately it was still under warranty) 

Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs notail          0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2       /media/windows  reiserfs notail      	0       0

Please help me, I don't want to change the Combo drive again... ](*,)

---

### Post by f.prisson on 2005-05-21
Does ```
mount /media/cdrom0
``` produce any output?

---

### Post by tseliot on 2005-05-21
[QUOTE=f.prisson]Does ```
mount /media/cdrom0
``` produce any output?[/QUOTE]

It attempts to read it many times. After several times, here's what I get:

mount: No medium found

---

### Post by f.prisson on 2005-05-21
Hm, looks bad I think...

---

