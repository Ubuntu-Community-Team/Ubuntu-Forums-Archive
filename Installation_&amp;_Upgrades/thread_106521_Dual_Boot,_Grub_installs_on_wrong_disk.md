---
title: "Dual Boot, Grub installs on wrong disk?"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by yay4furryanimals on 2005-12-20
Sorry if this is a repost, I did a quick grep and couldn't find anything specifically for this.

My system originally had two drives, one SATA and one IDE both primary.  I had the boot order set to boot up the SATA (on channel 3) instead of IDE (channel 0) to boot my x64 installation.  I also left about 25gigs knowing I'd be installing linux.

So in goes ubuntu. installed on the free remaining space on SATA channel 3 (sda).  Grub now wants to install, but it installs on my extra hd0 ide channel 0!  Causing my system to be unbootable from the sata drive.

Is this a bug, or is there something I could have done?  It'snot a major issue, it just might confuse someone else, I did the install twice thinking I screwed something up.

-
Chris

---

### Post by Sutekh on 2005-12-21
During the installation did you let GRUB choose where to install itself?  Or did you tell it where to go?  I think automatically, it would choose the IDE over the SATA drive.  

You can manually set-up GRUB on the SATA drive if you wish.  [Re-install GRUB]("http://ubuntuforums.org/showthread.php?t=24113")

Just follow the first post.  It's like re-installing with-out re-formatting, all you do is get the install CD to re-install GRUB.  When you get to the install GRUB stage, tell it to go on /dev/sda.

---

