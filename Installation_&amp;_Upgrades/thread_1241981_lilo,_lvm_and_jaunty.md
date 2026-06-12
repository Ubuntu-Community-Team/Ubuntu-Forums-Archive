---
title: "lilo, lvm and jaunty"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by onlyconnect on 2009-08-16
I'm running Ubuntu server with an LVM and mdadm RAID configuration - I have a RAID 1 array for /boot and a RAID 5 array for everything else.

I've successfully upgraded the kernel several times, but when I upgraded to 9.04 Jaunty it broke. Lilo got to "BIOS check successful" then crashed with an INT 14 error.

After fiddling around with a Knoppix live CD I've got it working again. What I had to do was to revert to the 2.6.27.14 kernel. The problem appears to be some fatal interaction between Lilo and 2.6.28.14.

Two questions: 

1. Is there any harm in continuing indefinitely with the older kernel? will updates foul it up at all?

2. What about grub2 - might that work with my setup and the newer kernel?

Tim

---

### Post by onlyconnect on 2009-08-16
... or if anyone has any ideas about how to fix the crash, that would be good too :-)

Tim

---

### Post by onlyconnect on 2009-08-17
It occurs to me that I'm wrong to assume Lilo is to blame for this, it could be some other problem with the updated kernel and my PC - motherboard is Intel D945GNT. For example, my problem may be similar to these:

[https://answers.launchpad.net/ubuntu/+source/linux/+question/69169](https://answers.launchpad.net/ubuntu/+source/linux/+question/69169)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554/+viewstatus)

Hmmm, I think some experiments with a Live CD are called for.

Tim

---

### Post by onlyconnect on 2009-08-17
9.04 desktop live CD works. Kernel 2.6.28.11-generic vs 2.6.28.14-server - still, maybe it is connected with Lilo and/or LVM+RAID?

Tim

---

### Post by onlyconnect on 2009-08-20
Hmmm, hasn't drawn a big response :-)

I'm going to try Grub 2 when I get a moment.

Tim

---

