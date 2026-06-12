---
title: "Ubuntu paritioner does not see Windows Vista OS for dual boot setup"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by rotithor on 2009-08-27
I have a sony VAIO laptop (VGN-CR220E) on which I am trying to dual boot Ubuntu 9.04 with Windows Vista Home premium. When I start the installer and it looks at the existing partitions it says "No OS installed" so it does not see windows Vista loader (I saw in the tutorials and videos related to this that the partitioner should see the Vista loader). It shows /sda1 with 7.5G and /sda2 with 178G. Do we know what the reason for this is and how to make the partitioner see Vista loader? My suspicion is without seeing that, it will not do the right thing for setting up dual boot.
Thanks in advance for helpful tips

---

### Post by fela on 2009-08-27
I'd say just install it (careful not to overwrite windows). Then when it's done, you can add the entries manually to /boot/grub/menu.lst. Assuming windows is on the first partition of the drive it would be (in the grub menu right at the end):

title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

At least that's what I THINK it is. No warranties included! Although you can't break your system like this, if it's wrong it would just be a dud boot entry that you can get rid of.

---

### Post by Mark Phelps on 2009-08-27
Is this the same problem as in your other thread? If so, read my response there.

---

