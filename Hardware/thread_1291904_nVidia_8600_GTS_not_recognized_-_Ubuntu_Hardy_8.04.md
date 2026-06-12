---
title: "nVidia 8600 GTS not recognized - Ubuntu Hardy 8.04"
date: 2009-10-15
forum: Hardware
---

### Post by swineflublues on 2009-10-15
I just installed hardy onto my Dell a few days ago, I've tried several methods to get my nVidia 8600 GTS to completely work with the GNOME display, but all attempts have failed. (I want my hardware acceleration for desktop effects and music visualizations) Initially when I installed Hardy, I selected to enable the restricted nvidia driver, and everything worked fine until I did a full reboot.  After the reboot, it seemed to have not detected my video card, was running in low-res 800x600, and there was no longer an option to disable the restricted nvidia driver.  I have tried many other methods of getting my card to work such as Envy, installing the drivers from the nvidia website, and downloading the various driver packages from the package manager.  I am pretty new to ubuntu, having tried it on the live CD a few times before, and I am in no case an experienced linux user.  

Any help would be greatly appreciated, especially some dumbed down step-by-step instructions.

---

### Post by Giblet5 on 2009-10-15
Did you install the restricted hardware driver?

What happens when you open a terminal window and execute ```
nvidia-settings
```

---

### Post by swineflublues on 2009-10-15
Haha... thank you so much Giblet.  I ran nvidia-settings, it told me to run nvidia-xconfig.  I verified that it had edited xorg.conf correctly and restarted and my problem was solved.

For everyone out there!:

If you are having trouble using you nvidia graphics card with Ubuntu 8.04 (Hardy Heron)
make sure you do these simple things first!

1.  Don't use System-Administration-Hardware Drivers and don't enable.
2.  Research the required package for your specific sound card to be installed by the Synaptic Package Manager.  Install it, man.
3.  Make sure you get a good install!
4.  Go to terminal and enter:
```
nvidia-settings
```This will let you know if you have a good entry for you nvidia card in your x-server config file.
5.  If it says you dont appear to have the nvidia driver installed, enter this into terminal:
```
nvidia-xconfig
```This will update your x-server configuration file so your nvidia driver will boot after restart.
6.  Reboot and hope for the best!

Thanks again Giblet!

---

