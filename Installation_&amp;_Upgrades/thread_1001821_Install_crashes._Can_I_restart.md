---
title: "Install crashes. Can I restart?"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by rewolff on 2008-12-04
Hi, 

My install crashed, so I restarted it, and got just a teeny little bit further before bombing out. I checked my CD for defects, and it checked out OK. On the other hand, the first time it bombed, I did have some IO errors on the CD drive. 

In any case, it didn't finish setting up GRUB, so the system was not bootable. Attempting to at least make it bootable by hand led to the problem that I don't know how to label my root partition with UUID, and that specifying root=sda1 to just get the d**n thing booted leads to a syntax
error. (Hmm. Maybe I should've said: root=/dev/sda1, but normally, at least for the kernel, simply sda1 just works)... 

Anyway, going through the whole install again, just for it to bomb out near the end is taking a lot of time, Can I restart the installer someway after it installed all the packages ?

Oh. For reference, I install by saying: "start ubuntu without modfiying my computer" and then click on install. This allows me to mess around a bit, and configure the network while the install is running. The first time, I needed to move the old debian install out of the way. Lucky I did, because now the system still boots debian...

---

### Post by mikewhatever on 2008-12-04
I think root=/dev/sda1 is correct, but if GRUB didn't get installed, there would be nothing to load the kernel anyway. Try re-installing GRUB from the live cd. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by rewolff on 2008-12-05
I remember walking through the kernel code, and it would strip off /dev/ at the beginning if present. Indeed, it seems that this code has broken over the last few years. On the other hand, the kernel need not parse this anymore, as it should mount and start off the initrd, and it seems the initrd got confused.

[edit] OK. Got it to boot. I found that I can use vol_id --uuid /dev/sda1 to find the uuid of my sda1 drive and then use that in "root=UUID=...." to specify the root fs. I'm now typing this on 0.75 Mpixels of screen instead of my normal 3.25, but I'm getting there....

---

