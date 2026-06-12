---
title: "Another SATA Thread"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by Bondolon on 2005-08-19
I feel like a heel for doing this, but I can't handle it any more...  I've been all over the internet (lol) and can't figure this out.  I have an ASUS A8N-SLI board, not the deluxe or anything.  I have SATA, onboard, which seems to work through the BIOS... "neat", I thought to myself when I got it.  I've been running fedora for a while, but got tired of it, and since I have been using Ubuntu on every other computer I have, decided to switch.  Problem being, even though everything else works *perfectly*, except for the SATA.  When I boot, I have the sata in my FSTAB:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hdb1       /home           ext3    defaults        0       2
/dev/sda1       /storage        ext2    defaults,umask=0222        0       3
/dev/sdb1       /movies         ext2    defaults,umask=0222        0       3
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

And it just won't mount or fsck.  It takes me to a shell, and I have to CTRL-D out, and then it just doesn't mount.  It says that /dev/sd* don't even exist.  Fine.  Whatever.  Let's move on to login.  I login... SHOCK AND AMAZEMENT.  /dev/sda and /dev/sdb are bright and shiny. sitting there. not mounted.  So I look at my /etc/modules, thinking I'll change it a bit:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
nvidia
``` 

oh wait, what was that module(s) again?  Not there, and I don't know what it is.  So, does anyone know what kind of SATA the A8N-SLI uses, and if so, what module(s) does that translate to?  Thanks in advance.

---

### Post by Bondolon on 2005-08-19
never mind, I got it.  I had to use sata_nv, with libata, as well as scsi_mod and sd_mod

---

### Post by gordyt on 2005-08-23
[QUOTE=Bondolon]never mind, I got it.  I had to use sata_nv, with libata, as well as scsi_mod and sd_mod[/QUOTE]
 Would you mind posting what your updated /etc/modules file looks like?  I think I'm having the same problem.

Thanks!

--gordon

---

### Post by gordyt on 2005-08-23
Oh Heck, that was easier than I thought.  Bondolon, please disregard my post.  You gave me enough clues to figure this out and I thank you for it!

I have a Mach Speed motherboard for my AMD64 system.  It uses the VIA K8M800 chipset.  I added the following two lines to /etc/modules:

scsi_mod
sata_via

Now all is well!

--gordon

---

