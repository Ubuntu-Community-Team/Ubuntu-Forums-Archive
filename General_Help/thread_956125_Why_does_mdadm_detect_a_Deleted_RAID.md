---
title: "Why does mdadm detect a Deleted RAID?"
date: 2008-10-22
forum: General Help
---

### Post by wbrunskill on 2008-10-22
I'm having problems with setting up a raid 5 on a M3N78-pro motherboard with 6 sata HDD (640Gbytes). Initially I set it up using the bois raid controller, this turned out to be a fakeraid.  So after install Dmraid I tried to make this bootable.  This failed, I had no luck there. So I decided to delete the raid 5 arry and just use one drive for boot and the other 5 for RAID 5.  However I remove DMRAID (actually I reinstalled) and got the boot drive all good.  However when I try and set up a RAID 5 on the 5 spares, all is good on creation and is useable straight away.  The problem is when I reboot the system GRUB (I think) detects the old raid settings and tries to boot of it, fails but because mdadm has started it has decided that the boot disk is still part of the array it will not continue and initfsram is started.

I've tried erasing MBR using DD =if/dev/zero =of/dev/sd[a-f] count 512 or something like that.

Basically I cannot now set up a raid once I have initially installed the base system.  BTW its mythbuntu 8.04 with all the lastest updates.

Any help?
Cheers
One confused linux lover.
Wayne.

---

