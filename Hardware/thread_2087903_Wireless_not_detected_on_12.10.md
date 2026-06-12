---
title: "Wireless not detected on 12.10"
date: 2012-11-24
forum: Hardware
---

### Post by CompSciSTL on 2012-11-24
Hello,

I'm back to using Linux after an absence.  This time around I thought I would give Xubuntu a try.  (I'm not a fan of the new desktop in Ubuntu and the Desktop reminds me a lot of the older Gnome desktop).  After installing Xubuntu 12.10 on my Acer Extensa 5420, I am noticing that it is unable to detect my wireless internet.  Now, I do recall having this issue with a previous version of Ubuntu, and it seemed to involve either a trip to the terminal and/or possibly making a change to a settings file.  Could anyone perhaps refresh my memory on this?

Thanks!

PS
According to the Additional Drivers tab of Software Sources in the Software Updater menu, I have the Broadcom 802.11 Linux STA (BCM 4311) driver installed.

---

### Post by ahallubuntu on 2012-11-24
You can try this:

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

FYI, there's a separate "Networking & Wireless" section now.  An admin will probably move this thread there.

---

### Post by CompSciSTL on 2012-11-24
Hmm...seemingly no luck so far.  I tried the link as suggested.  At post #7 of that forum link, I tried the terminal commands mentioned.  When I tried to install or reinstall the bcmwl-kernel-source I'm seeing the following errors in the terminal:

Module b43 does not exist in /proc/modules
Module b43legacy does not exist in /proc/modules
Module ssb does not exist in /proc/modules
Module bcm43xx does not exist in /proc/modules
Module brcm80211 does not exist in /proc/modules
Module brcmfmac does not exist in /proc/modules
Module brcmsmac does not exist in /proc/modules
Module bcma does not exist in /proc/modules

It sounds like something may not installed correctly even though it "says" I have the driver installed.  Any ideas?  :confused:

---

