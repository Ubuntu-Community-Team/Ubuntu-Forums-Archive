---
title: "installing ubuntu on a hardware raid"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by cykotiktek on 2009-06-28
I am running a p5n-d motherboard with 2 x 120 gb sata drives in a raid 0 configuration.  When i try to install ubuntu it does not see the raid it sees the drives as seperate drives.  When i do install it grub gives me an error 23 which i have read is not an altogether good thing and blows away the MBR for the windows 7 install on the drive.  How should i go about getting this installed?

---

### Post by ronparent on 2009-06-28
Try the alternate install cd. It contains the software for addressing the raid during install.

---

### Post by cykotiktek on 2009-06-28
sorry i forgot to mention i have tried intrepid 64 bit and jaunty 64 bit

---

### Post by cykotiktek on 2009-06-28
I could install this on another drive in my computer thats not a big deal either but wouldn't grub still have to write to the raid to set the boot?  or could i put it on the other drive change that drive to boot first and the raid to boot second but would grub still detect the windows 7 install?

---

