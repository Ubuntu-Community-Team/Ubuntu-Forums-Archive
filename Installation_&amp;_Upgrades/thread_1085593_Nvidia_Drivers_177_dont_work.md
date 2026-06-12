---
title: "Nvidia Drivers 177 dont work"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by zexelon on 2009-03-03
I have a Nvidia 7800GTX video card. On a fresh install of Ubuntu 8.10 (with all updates applied) xorg works with the freeware nv driver. However when I enable the recommended Nvidia 177 Forceware drivers xorg dies. 

After rebooting the screen flashes a couple of times and then dumps me to a standard tty terminal. I have even tried the Nvidia 180 drivers and the same thing happens. I cant even get xorg back working with the default nv driver after I do this, I have tried running "#dpkg-reconfiger xserver-xorg" and while this does change the xorg.conf file back to default, xorg simply flashes the screen a couple of times and then dumps back to tty. The exact error is EE No Devices found. This is the only error I get when I try to startx. 

Any help in getting this working would be much appreciated.

---

### Post by dburnett77 on 2009-03-03
> **zexelon said:**
> I have a Nvidia 7800GTX video card. On a fresh install of Ubuntu 8.10 (with all updates applied) xorg works with the freeware nv driver. However when I enable the recommended Nvidia 177 Forceware drivers xorg dies. 

After rebooting the screen flashes a couple of times and then dumps me to a standard tty terminal. I have even tried the Nvidia 180 drivers and the same thing happens. I cant even get xorg back working with the default nv driver after I do this, I have tried running "#dpkg-reconfiger xserver-xorg" and while this does change the xorg.conf file back to default, xorg simply flashes the screen a couple of times and then dumps back to tty. The exact error is EE No Devices found. This is the only error I get when I try to startx. 

Any help in getting this working would be much appreciated.

After installing, run 'sudo nvidia-settings' and see if it did install, correctly.
If not, run 'sudo nvidia-xconfig' and see if that does it.

---

### Post by zexelon on 2009-03-03
I have done both of these items, however neither one worked. The nvidia-xconfig command did write a new xorg.conf file, but it still would not run...

On a side note however I think that I have found the solution, I actually have two video cards in my system a 7800GTX mentioned above and a Nvidia 7300 something that I forgot about because I havent used it in a very long time (used to run triple monitors).

I found in an [**_older post_**]("http://ubuntuforums.org/showthread.php?t=966315&highlight=nvidia+177&page=2") that people with multiple cards need to manually add the BusID setting to the xorg.conf file. 

I forgot about this setting from the last time installed Linux, I am going to give it a try when I get home from work, but I am fairly certain it will fix the problem.

---

### Post by zexelon on 2009-03-03
So this fixed my problem. Thanks to the people in the above linked post for their knowledge.

---

