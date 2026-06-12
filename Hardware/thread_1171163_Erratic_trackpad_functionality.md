---
title: "Erratic trackpad functionality"
date: 2009-05-27
forum: Hardware
---

### Post by NikAmi on 2009-05-27
To begin, I hope this is the correct thread for this question.

I have a Lenovo Thinkpad T61 with multiple partitions so as to dual boot. I recently upgraded my Ubuntu installation to Jaunty using a fresh format and install. I then set out to add all the little packages that would give full me functionality of the hardware in the laptop. I installed tp-smapi, the latest stable xserver-xorg-video-intel from the ubuntu-x-swat PPA, and some other stuff. I then saw the article in the Wiki about the Intel video performance and, as the article suggested, installed the 2.6.30 rc7 image and edited the xorg.conf as indicated. I also enabled Compiz.

After all this, my trackpad started acting up. It works fine when using the desktop menus or over certain programs such as the terminal, but when I go over the desktop or other programs such as Firefox, the cursor slows to a crawl. What's really weird is that the touchpoint (red nubbin) is not affected at all and zooms around the screen at the proper pace no matter what it is over.

Anyways, I have tried everything I can think of. I have changed the speed settings in the Ubuntu mouse management program, installed GSynaptics and changed the settings in that program, turned off Compiz, uninstalled the RC kernel, set the xorg.conf back to its original configuration, dpkg-reconfigure xserver-xorg. Nothing works and because the trackpoint works flawlessly, I am pretty sure that this problem is limited to the mouse driver, its configuration, or HAL (that's what takes care of the mice and keyboards now right?). If anybody has any ideas, I would really appreciate them. Thanks in advance!

---

### Post by NikAmi on 2009-05-28
Does anyone have any ideas? Any input helps...


Well, not *any* input, but I still hope someone can help. :D

---

