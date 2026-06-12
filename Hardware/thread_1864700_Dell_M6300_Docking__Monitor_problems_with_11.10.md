---
title: "Dell M6300 Docking / Monitor problems with 11.10"
date: 2011-10-19
forum: Hardware
---

### Post by kwildman on 2011-10-19
Got some weird stuff going on here with the 11.10 upgrade.   Dell Precision M6300 with NVIDIA QuadroFX 1600 graphics card.   During initial install had problems with drivers locking up during boot ans was able to fix this with installing NVIDIA current from bash.

Laptop runs fine and looks great when it is undocked.  Nvidia settings manager fully functional and shows TV-O and DFP-0 without issue.  Am abel to see Xserver Display Configuration ok.

When i dock the laptop with the lid closed to use my Dell Monitor via DVI from the dock there was no display.   Open lid and laptop monitor display was on.  Go to NVIDIA settings manager and it is all jacked up - the XSERVER Display configuration is unaccessible and no info is displayed.   TV-O, DFP-O not displayed, etc.  So i manually edited xorg.conf file to use DFP-2 as default.   Rebooted and all was well - display on external monitor with lid closed.   However, next time i booted with laptop on dock i get a   weird unity desktop - top bar is totally different, differnt icons, slate grey color.  The Unity launcher is not displaying all icons on the bar.  Some are there but there are blank spaces where there should be an icon...clicking on a blank space activiates the application that should be there.   If i reboot with the laptop undocked everything is beautiful.   Retried on dock and 1 time out of about 20 it came up normal on the dock.  Have not been able to get it to come up without the jacked up unity since then.  

The dock appears to be affecting what hardware is detected and also makes the Nvidia-settings manager unusable.   This setup has worked without issue since Intrepid.  

As always, any help would be greatly appreciated.

---

