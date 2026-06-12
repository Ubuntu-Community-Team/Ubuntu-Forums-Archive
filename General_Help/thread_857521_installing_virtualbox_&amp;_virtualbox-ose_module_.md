---
title: "installing virtualbox &amp; virtualbox-ose module breaks sound system and nvidia driver"
date: 2008-07-12
forum: General Help
---

### Post by bogdanbiv on 2008-07-12
I installed  "virtualbox-ose module for linux-image-generic" and "virtualbox-ose module for linux-image-2.6.24-19-generic"  

After I installed the packages I restarted the PC only to find gtkdisplaycfg (the failsafe X server configuration application).
After I set up my system back in a usable state (using the nv driver) I had found out that KMix keeps complaining that there is no sound mixer.
Also there is a popup telling me "xine was unable to initialize any audio drivers".

How do I repair the sound system?
My system:
Kubuntu 8.04

$ uname -a
Linux bog-desktop 2.6.24-19-386 #1 Wed Jun 18 14:09:56 UTC 2008 i686 GNU/Linux

---

### Post by sdennie on 2008-07-12
Is there a reason you are using the -386 kernel instead of the -generic kernel?  That could have caused your problems.  Make sure you select "2.6.24-19-generic" when grub comes up (you may have to hit escape to get into the menu).  You may also want to uninstall the -386 kernel to prevent future confusion.

---

### Post by bogdanbiv on 2008-07-13
I selected 2.6.24-16-generic kernel at boot time: sound automagically works!
Initially I thought it was something unrelated to my sound problem, but you were right, it was a kernel problem. Lucky me posting my kernel config and you spotting it.

It does not have to do anything with virtualbox - there were just my sloppy hands at work. :-)

Thanks a ton for it!

---

