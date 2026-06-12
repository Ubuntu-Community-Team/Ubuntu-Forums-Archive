---
title: "[SOLVED] why does ubuntu freak after reinstalling 3rd OS"
date: 2008-10-20
forum: General Help
---

### Post by peedeeramone on 2008-10-20
Okay ive got a triple boot system:

sda1:ubuntu
sda2:xp
sda3:swap
sda4:extended
sda5:fedora

sda5 used to have sabayon. i use the last partition for a constantly changing alternate os. when i install something new on that partition ubuntu freaks out (i probably have it set to automount) halfway through the boot process and brings me to a terminal (that i can skip to resume booting). 

my question is probably simple: what do i run to fix it (fsck maybe?) and what can i do in the future to prevent this?

mucho gracias (in advance)


PD

---

### Post by louieb on 2008-10-20
Most likely when you install something new in sda5 it UUID changes. Things like formating a partition before installing a new OS will change the UUID. 

Check** /etc/fstab** I'd just comment out the entry for sda5 and let it mount on demand.

---

### Post by peedeeramone on 2008-10-20
is it possible to just remove the UUID but leave the rest of the entry? I would still like the drive to automount if it wouldnt be a big deal.

---

### Post by peedeeramone on 2008-10-20
ive got it pretty much fixed. i just manually put in the fstab config for it and it worked.

for other's future reference heres what i did: basically i deleted the UUID and replaced it with /dev/sda5 then filled in the rest from the guidelines displayed at the top of the file: /media/firebird [just the mountpoint i created for the previous installation]   ext3 [filesystem type]   defaults [options] and left the dump and pass numbers that were allready there as i dont really know what they do.

---

### Post by louieb on 2008-10-21
[quote=peedeeramone;6002031deleted the UUID and replaced it with /dev/sda5 [/quote]

Glad you got it working.  :)

---

