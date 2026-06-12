---
title: "Going to upgrade, but 1st..."
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2009-11-01
I had a system crash early part of the year, so I reinstalled, but now when I reboot, there are about 6 different kernels I can boot up with.  What's the best way to clean things up and then upgrade?

---

### Post by craig.o on 2009-11-01
> **Daremo_06 said:**
> What's the best way to clean things up and then upgrade?

That's a big question ;)  The best way for you to cobble together a good answer probably starts [here.]("http://ubuntuforums.org/showthread.php?t=1305158")  Glance over that and if it doesn't answer your question, you should probably post back with your system info.  Otherwise the question remains very broad.

hth,
-Craig

---

### Post by 73ckn797 on 2009-11-01
If you are going to do a fresh install it will take care of itself. If you upgrade other issues could occur. Do some searching regarding the advantages/disadvantages between fresh versus upgrade.

If you want to clean out the old kernels you can go into Synaptic and find the kernels to uninstall. You could also edit "menu.lst" and delete the additional kernels from the list. Karmic Grub2 does the boot selection differently so you will not be able to edit as before.

See this link about Grub2: [https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)

---

### Post by Turtle.net on 2009-11-01
You can either try the computer janitor (System->Administration->) and see if it suggest you to remove some packages (and the additional kernels).
If not you can search for the additional kernels directly in syanptic and remove them.
Your system will not be affected as long as you keep linux-image generic (that's a meta package that will automatically poin to the newest kernel).
Anyway, I think that the upgrade will not be affected by that, since the upgrade will change the kernel for the Karmic version.

---

