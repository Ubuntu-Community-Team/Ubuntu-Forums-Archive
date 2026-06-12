---
title: "BIOS: Primary drive 1 not found"
date: 2009-05-01
forum: Hardware
---

### Post by Open-SuSe-A-Me on 2009-05-01
Hello, i have a Dell Dimension 2400 desktop, and since i;ve owned it this message pops up in the bios on boot "Primary drive 1 not found, strike the F1 key to continue" and i have to press it for grub to load.  This happened even back when the PC just had XP on it.  Ubuntu works fine, just wondering if anyone knows why this happens?

---

### Post by Open-SuSe-A-Me on 2009-05-02
bumpity bump

---

### Post by zorbawic on 2009-05-04
well, this is not an OS issue - this is a hardware issue.
Recently I had a similar one when my hdd broke down.
First thing that came to my mind is that either Your motherboard has a problem with detecting the hdd so I'd suggest to get a new version of the bios and flash the mobo.
Second thing is that Your bios might have something mis-configured in its hdd section (if it has it) like S.M.A.R.T. configuration or Ultra DMA, 
OR Your hdd is the reason - so if it would be possible for You to swap it with another one that works fine (preferably from other manufacturer) to see if the situation changes. Another thing is to get UBCD and check the hdd for errors with MHDD - maybe this will help.

One more thing - sometimes the bios just doesn't like when there is no hdd plugged as primary. It's because some old OS's won't want to install on other than primary I guess.

---

### Post by cbsp01 on 2009-05-06
This is a known behavior with DELL computers. You probably need to reinitialize your BIOS, because your drive configuration might have changed, which would explain the message. The procedure is:

1) reboot the computer and press F2 during rebooting : a window will open with BIOS configuration options.

2) strike successively:** ALT-E**, then **ALT-F**, then **ALT-B** : this sequence will start BIOS re-initialization, in particular the identification of the drives on the IDE bus. It will take some tens of seconds. Then reboot will resume and the problem is supposed to be solved :smile:

Good luck.

---

### Post by gijake on 2010-09-22
Extremely useful to know this was the whole problem with install.  On a dell dimension 2400.  the bios needs to be reset in order for the install to proceed properly.  ** ALT-E**, then **ALT-F**, then [B]ALT-B to get the drive to be recognized.
[/B]

---

