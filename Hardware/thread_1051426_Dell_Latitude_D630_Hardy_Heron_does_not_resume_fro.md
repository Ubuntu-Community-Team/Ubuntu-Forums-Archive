---
title: "Dell Latitude D630 Hardy Heron does not resume from hibernation"
date: 2009-01-26
forum: Hardware
---

### Post by misha680 on 2009-01-26
Fresh install of Hardy Heron on a Latitude D630 with Nvidia graphics card (135m I think). Hibernation (sudo pmi action hibernate) - computer goes to sleep successfully (swap partition is a little larger than physical ram of 4 GB), but upon wakeup I get normal startup rather than resume of hibernation state. Suspend works fine.

Any help appreciated.

Thank you
Misha

FIXED: 
```
sudo gedit /etc/initramfs-tools/conf.d/resume
```
put in a line:
```
RESUME=UUID=PUTYOURSWAPUUIDHERE
```
the swap UUID comes from /etc/fstab. Finally:
```
sudo update-initramfs -u
```
Voila. Hibernate works.

---

### Post by nemoinis on 2009-05-12
Thanks misha680, I had the same problem on a Toshiba Satellite running Jaunty, and that fixed it.

This may help other users: the resume UUID that was in /etc/initramfs-tools/conf.d/resume  was not the correct one on my system.  After fixing it, I realized why: I had migrated (via dd) this system from the original hard-drive to a new bigger drive.  And of course the swap partition on the new drive has a new UUID. 

Something to remember when cloning laptop drives...

---

### Post by inigoml on 2009-06-18
Yes, it works! I love you. ;-) Thank you very much. I was a logic fix...I should have thought about it before. :)

---

