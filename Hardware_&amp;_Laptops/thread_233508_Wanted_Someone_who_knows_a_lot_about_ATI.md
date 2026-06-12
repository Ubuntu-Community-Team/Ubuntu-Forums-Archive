---
title: "Wanted: Someone who knows a lot about ATI"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by Archangel_X19 on 2006-08-10
I mean a whole lot.  Because I've gone to great lengths to make sure that my video card works.  And before recently, Ubuntu and other OS's it really worked.  Anyway, brief history on what I've done.  Followed the ATI driver wiki to the letter on both 2.6.15 kernel and 2.6.17 kernel I compiled.  I got successful installs on both of them.  The only thing is that when I boot up from a perfect ATI install it boots all the way up to when X starts.  And X tries to start but then goes to a blank black screen and completely freezes.  I have to turn off the computer by holding down the power button.  No amount of ctrl+alt F1, backspace, or delete will save me then.  But the odd thing is that when I check the log files for when it boots to a blank screen it tells me that DRI and all acceleration is enabled and working.  I've checked the Xorg.0.log and the Dmesg log.  I even checked the messages log and can find no errors when it's booting to a blank screen.  I tried these drivers under archlinux and the only time it acted like this was when I made intel_agp load first in the rc.conf file the computer would boot to a blank screen like it is now.  But when I took intel_agp out of loaded modules I had no 3D acceleration but I had 2D acceleration and an error in my Xorg.0.log that said "XF86_ENODEV".  I've changed my ubuntu xorg.conf file and I can't get a screen on anything but vesa being the driver.  I've tried aticonfig and dpkg-reconfigure xserver-xorg choosing both fglrx and ati but to no positive outcome.  If its ATI's drivers that's fine.  I just want to know it's not me and that there is nothing I can do.  I'll have my specs at the bottom of this post and if requested I can post any logs or files needed to be seen.  I appreciate any help I can get.  I've googled the net dry so this is a cry for help.  Thanks again for any help that can be provided cause I know this is only the 300th post you've read on ATI.

Intel Pentium 4 3.0 HT
1 gig DDR2 RAM
Radeon X800 Pro
Dell M782 Monitor Horiz: 30-85  Vert:50-160 Resolution: 1024x768
Ubuntu 6.06 Kernels 2.6.15-26-686 out of the repos and 2.6.17 (tried both)

---

