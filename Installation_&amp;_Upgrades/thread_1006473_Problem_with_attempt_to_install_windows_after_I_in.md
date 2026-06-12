---
title: "Problem with attempt to install windows after I installed Ubuntu"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by peterponder on 2008-12-09
Hi what I know of computers is dangerous but I jumped in and installed Ubuntustudio but deleting my windows data (on purpose) etc when I partitioned my HD.
Ubuntu is running fine but need Windows programs which are not supported by Wine. I therefore want to reboot with my Windows Vista CD to install.
If I do a reboot now (F12 setting CD drive as my boot drive) the system simply ignores this and goes straight into the HD boot sequence and starts Ubuntustudio. 
However when I insert the Ubuntu CD and set my booting sequence to CD drive the Ubuntu CD starts etc.
I have no experience of shell etc and have been floundering around with the UbuntuStudio partitioning which I have done several times now.
BTW the Grub file has been loaded.
Can anyone guide me on the right track here. Not to much techlanguage though.

Thanks

---

### Post by Pumalite on 2008-12-09
Could you post:
sudo fdisk -lu

---

### Post by Jon@bayleys.org.uk on 2008-12-09
These may be totally irrelevant, but a couple of things spring to mind, firstly, is your copy of Vista, ahem, legal?  If its a copy it may not actually be a bootable image. second thing is, and I'm sure you've checked this, is your optical drive a DVD drive or only a CD drive? Only Vista comes on a DVD whereas Ubuntu is a CD. sorry, if I'm being patronising

Cheers,

Jon

---

### Post by Mark Phelps on 2008-12-10
The question about whether it's a Vista "CD" or "DVD" is actually an important one because, if it's a "CD", and it came with your system, it's probably only a recovery disk.

However, if your system came preinstalled with Vista on it, the recovery CD can probably be used to restore your original Vista installation -- but that will wipe EVERYTHING from your drive in the process.

---

