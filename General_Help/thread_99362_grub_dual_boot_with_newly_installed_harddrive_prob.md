---
title: "grub dual boot with newly installed harddrive problem"
date: 2005-12-05
forum: General Help
---

### Post by ugly_b on 2005-12-05
I recently installed a new harddrive on the ide for Windows.  Ubuntu is installed on the sata.  But I can't get grub to boot to the Windows drive  :(
My /etc/fstab looks like this:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               reiserfs notail          0       1
/dev/sdb1       /d              reiserfs defaults        0       2
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /windows        ntfs defaults     0       1

```
So, I can read the Windows installation drive from Ubuntu with no problems.

And my /boot/grub/device.map looks like this:
```

(hd0)   /dev/sda
(hd1)   /dev/sdb

```
From reading some threads, I think I have to edit this to somehow include hdb.  But, what do I put here?...and do I have to reinstall grub afterwards?

Here's my Windows portion of /boot/grub/menu.lst:
```

title           Crappy WindowsXP
root            (hd4,0)
makeactive
chainloader     +1

```

I've tried fiddling around with the "root" line with many combos of numbers but nothing works.  Can any experts give me a step-by-step to fix this?  I've gotten tired of switching primary through the bios.
Thanks for any help.

---

### Post by ugly_b on 2005-12-06
All fixed using the following in my /boot/grub/menu.lst file:
```

title              Crappy WindowsXP
map             (hd0) (hd1)
map             (hd1) (hd0)
rootnoverify    (hd1,0)
chainloader     +1

```

---

### Post by KermitJr on 2005-12-07
[QUOTE=ugly_b]All fixed using the following in my /boot/grub/menu.lst file:
```

title              Crappy WindowsXP
map             (hd0) (hd1)
map             (hd1) (hd0)
rootnoverify    (hd1,0)
chainloader     +1

```[/QUOTE]

This is a nifty trick I've used before.  You can install windows on a C: drive and then simply move it to the slave and remap it via GRUB.  Works like a charm and no boot loaders on the windows drive... it stays, em, "pure"

---

