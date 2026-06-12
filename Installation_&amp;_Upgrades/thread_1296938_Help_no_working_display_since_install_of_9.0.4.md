---
title: "Help no working display since install of 9.0.4"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by shazzer on 2009-10-21
Im having a disaster. Upgraded to 9.0.4 couple of days ago have been on tons of forums hoping to get help. Had a problem with the display so used Envy to install an ATI driver as I didnt get a reply from anybody to help and no drivers recommended in the Envy menu so now dont have a working display. It freezes on boot up.  I have tried to revert to old kernel but none available, same problem only offered 9.0.4 in my boot menu.  Want to know either how to uninstall the ATI driver I put in, which I dont know what it was now or how to add a new driver but from the root menu using maybe a USB stick. 

Im desperate now - really need help on this one. Dont even know which driver I need. I have an EEPC 1000h.  Do I need NVIDIA or what? HELP< HELP< HELP!!

---

### Post by Mark Phelps on 2009-10-21
You really need to learn how to use Google to find out information about the stuff you own ...

According to a Google search, your machine has an Intel 915 processor.  Unfortunately, there are problems with 9.04 and Intel video chipsets, that AFAIK, are being fixed in 9.10.

So, with 9.10 just around the corner (Oct 29th), you would do better to wait until it comes out and install it.

---

### Post by shazzer on 2009-10-21
Thanks but how do I get anything working at all now? It was working until I used Envy to install the wrong driver. Is there any way to uninstall the wrong driver and install a new one that might work better?

I cant afford to wait as everything on my netbook now inaccessible! without display.

---

### Post by Mark Phelps on 2009-10-21
> **shazzer said:**
> Thanks but how do I get anything working at all now? It was working until I used Envy to install the wrong driver. Is there any way to uninstall the wrong driver and install a new one that might work better?

I cant afford to wait as everything on my netbook now inaccessible! without display.

The link below has instructions on how to remove the ATI driver.  After you do that, don't install a new driver, just reboot.  Ubuntu should then locate your video chip and install the Intel driver by default.

Link: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

