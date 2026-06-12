---
title: "Need help with either Geforce 7300gt or reinstalling nouveau"
date: 2010-12-16
forum: Hardware
---

### Post by psychosemantic on 2010-12-16
Using ubuntu 10.10

I tried to install the nvidia drivers for the 7300 gt and messed up horribly.  At some point I removed all of the nvidia and nouveau packages.  I would just like to get things back to how they were and use the nouveau driver, but I'm lost.  When I restart the computer, I get an error like

drm failed to open device 

and 

no devices detected

I'm pretty clueless and would greatly appreciate some help.  4 hours of this today is enough lol

---

### Post by Krytarik on 2010-12-17
Are you landing at the console login after that error? If not, boot in "recovery mode".

When you finally loged into the console, enter:
```
sudo dpkg-reconfigure --default-priority xserver-xorg
```
This should restore a default "xorg.conf".

Try to boot into the desktop after that and re-install the preferred driver.

You should also take a look at this HowTo about installing the proprietary drivers (if not already done):
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

