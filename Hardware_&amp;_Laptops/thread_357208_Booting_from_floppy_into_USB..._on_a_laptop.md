---
title: "Booting from floppy into USB... on a laptop"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by LeckyT on 2007-02-09
I've been using Xbuntu since forever on a VERY low end laptop.

I've not got my hands on a couple of P4 laptops, and want to do something a little different : they have no hard drives.

I can boot ok from a floppy, and then into an install CD, using SmartBootManager.

There is NO USB boot support in the Bios. And, it probably wont flash. No OS either.

I have one machine booted into Ubuntu from the CD, and I want to do the following:

 Make a Diskette with an MBR pointing to a USB stick (won't work, I realised, so...)
 Make a Boot diskette, with USB support, and mount the USB stick as root, and complete booting into ... Ubunu.

Is this possible, or I am I dreaming?

LeckyT

---

### Post by Mike_Longbow on 2007-02-10
It IS possible... in theory...
Is just that I don't know how... I would like to know, too.
I used to use [DSL]("http://www.damnsmalllinux.org/"), they have a [boot floppy]("http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies") that's used to boot the kernel from a USB flash drive. I've used it in my laptop (a really old one) and it works just fine.
But, as I said, this floppy is designed to work only with DSL (or at least I think so...), and I'm not sure if it can work with any other distros (i.e. Ubuntu)

---

### Post by LeckyT on 2007-02-11
Hi,

Nope - I tried that. The issue is that the Ubuntu install won't let you specify a FAT formatted drive to be mounted as root, and the DSL boot floppy expects root to be mountable from a FAT drive. Ubuntu insists (rightly, IMHO) that root must be located on a 'full-featured' Linux-aware partition.

The theoretical solution is to build a root floppy with USB support, and then point it at the USB drive to mount root. That's what DSL does. However, I have no clue as to how to use Ubuntu (running from CD) to create a boot floppy with USB support.

How is it usually done?

---

### Post by Mike_Longbow on 2007-02-11
> **LeckyT said:**
> How is it usually done?

I wish I knew... :confused:

---

### Post by XxPoseidoNxX on 2008-06-23
Hello
You could probrably do it using the sbootmgr.dsk
I have used to boot cds not usb-drives but you should try anyway
download it here:
[http://public.www.planetmirror.com/pub/slackware/slackware-9.0/rootdisks/sbootmgr.dsk](http://public.www.planetmirror.com/pub/slackware/slackware-9.0/rootdisks/sbootmgr.dsk)
 
and then just write it to the disk with
```
dd if=sbootmgr.dsk of=/dev/fd0
```

---

