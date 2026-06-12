---
title: "why can't I access previous version (7.10) after installing 9.04"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by mibungu on 2009-10-22
Hi, first I had ubuntu studio 7.10 (I believe or 7.04). After installing ubuntu 9.04 it locked the ubuntu 7.** version. I can log in the root account (other vanished) but can't use usb ports, etc... So even though I do something in that system there is now way I can put it on a usb stick or so..

The issue is, blender has been acting strangely on the 9.04 version. And I can't use it. In the older version (ubuntu studio) it works alrite and would just keep ahead using it. Since after installing ubuntu-studio karmic , grub didn't recognize the other systems and removed that again. 

So now I have a ubuntu 9.04, kubuntu 9.04 (wanted to see if it would make a difference) and the older ubuntu-studio which is locked. How can I unlock it. Or what have I done wrong while installing karmic.

sorry for two questions in one thread

mibungu:confused:

---

### Post by dstew on 2009-10-23
So, you can boot the 7.10 system, but cannot log into your old user account? If that is the case, perhaps you have a /home folder (partition?) that is being used by your newly installed system. If your new system account name is the same as your old system account name, probably preferences and settings were changed to work with the new OS. Since the software in the new OS is different, the new settings may cause the old software to fail. Just a guess. You should be able to use your old documents though.

If you want to use the old blender, try creating a new user in your old system with a different user name. See if then you can resurrect some of the old software.

---

### Post by mibungu on 2009-10-27
no separate home folder,
and all hw ports a blocked nothing mounts etc..  
Well strange this never happened before
might just reinstall the old 7.10 version and see what happens

---

