---
title: "Touchpad doesn't work on netbook"
date: 2010-09-19
forum: Hardware
---

### Post by DaizNaew on 2010-09-19
Hey all, i seemed to have run into a problem on my Packard bell dot S2 netbook. 
It seems my touchpad has stopped working, i have been running Ubuntu 10.10 maverick meerkat desktop for about 2 weeeks, without any problem. But after updating using 
```
sudo apt-get update
sudo apt-get upgrade
```
then restarting my computer, the touchpad no longer responds to anything, hitting fn+F7 foes nothing, neither does activating it in the gpointing-device program.
Could anybody try and help me with this? or tell what more info i need to post.

Thanks in advance ~ Daiz Naew

Edit: Fixed the problem by manually downloading the newest kernel update.

---

### Post by empoulator on 2010-10-06
I had exactly the same problem... The upgrade of Ubuntu 10.10 made my graphic card and touchpad not work any more. 

I've found the fix for the touchpad (on my Sony Vaio).  Credit goes to these threads:
 [http://ubuntuforums.org/showthread.p...ht=vaio+series]("http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series") Post #2
[http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series](http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series) Post #2

 Here's the fix:
 
 1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
 2. Run: sudo update-grub
 3. Reboot.


> **DaizNaew said:**
> Hey all, i seemed to have run into a problem on my Packard bell dot S2 netbook. 
It seems my touchpad has stopped working, i have been running Ubuntu 10.10 maverick meerkat desktop for about 2 weeeks, without any problem. But after updating using 
```
sudo apt-get update
sudo apt-get upgrade
```then restarting my computer, the touchpad no longer responds to anything, hitting fn+F7 foes nothing, neither does activating it in the gpointing-device program.
Could anybody try and help me with this? or tell what more info i need to post.

Thanks in advance ~ Daiz Naew

Edit: Fixed the problem by manually downloading the newest kernel update.

---

