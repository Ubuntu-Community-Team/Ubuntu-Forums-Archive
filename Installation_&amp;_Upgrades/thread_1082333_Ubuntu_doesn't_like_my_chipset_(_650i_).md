---
title: "Ubuntu doesn't like my chipset ( 650i )"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by beofres on 2009-02-27
Ahhh, where to begin.  I have a linux box acting as a DVR running ZoneMinder ([http://www.zoneminder.com](http://www.zoneminder.com)) on Ubuntu 7.10.  Decide to upgrade the application, and go with debian, but after trial and error with debian, which had poor support for the network card on my box, I decided to go with Ubuntu 8.10 Server.  Here are my system's specs:

ECS NF650iSLIT-A Rev. 1 with 2GB DDR-800 running a 2Ghz Conroe, 2 Western Digital 40GB IDE drives (one as a backup, not in RAID), and 3 Western Digital 500GB SATA drives attached to the onboard SATA interface on the mobo, running in nvidia RAID-5.

Now, the above configuration worked on 7.10 just fine, and did on Debian (minus the netcard issue and some issue with the cctv cards..go figure) but when I installed 8.10, repartitioned the original boot drive, installed, rebooted, locked up with "error 2" when trying to load GRUB.  Reinstalled in expert mode, installed LILO instead of GRUB, and was able to get passed that, but got stuck at the following screen:

[IMG]http://xanaduwapiti.net/ubunturz/IMAGE_004.jpg[/IMG]

So I unplugged the CD-ROM, and it dropped to the same message, only complaining about sde (the last RAID-5 drive in my array).  I sequentially moved each sata drive out, and after the third it booted fine.  So I figure there was some issue with 8.10 and my nforce chipset.  I repeat the installation process with 8.04 and same issue.  So....is there a compatability issue?  I'm not good with linux, kinda new, so if there is anything I should look at please, tell me.  I'd like to get this camera system back up pretty soon.

---

