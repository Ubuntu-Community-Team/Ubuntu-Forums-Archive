---
title: "CD-ROM problems"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by gnarly_buttons on 2007-08-28
I have installed edubuntu Feisty, but my cdrom drive isn't working.  When I put a cd in the drive, it makes a little noise to show that it's doing something, but then nothing happens.  This is what happens when I type in the following commands:

mount /dev/cdrom
mount: special device /dev/cdrom does not exist

My fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=d85eedbb-149d-46e5-80ec-d74aa0baadef / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=301bb18d-b459-48d0-b446-eb2e25c39519 none swap sw 0 0
/dev/cdrom        /media/cdrom0  auto   ro,noauto,user,exec    0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thanks for any help.

Scott

---

### Post by Marat Galiev on 2007-08-28
You must mount like this 
mount /dev/cdrom1 /mnt/cdrom

---

### Post by gnarly_buttons on 2007-08-29
I tried what you said, but I get this message:

mount: mount point /mnt/cdrom does not exist

Shouldn't it be /media/cdrom0 anyways, because of my fstab?  I'm not sure, as I'm not so familiar with Ubuntu.

Scott

---

### Post by rulix1 on 2007-08-29
I have a similar question:

in fstab I have to note the mount point of a device.

To date I was of the opinion, that this directory will be created by the routines behind fstab.

A manual mount I thought needs a value for the device, e.g.
mount /dev/hda3  /media/Daten 

If I put this as a part of the line in fstab and restart the comp.
I get the message no such directory.

It's an old comp. 
On my newer I never had problems with fstab.
Rudi

---

