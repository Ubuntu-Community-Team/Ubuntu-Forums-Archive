---
title: "Disabled my propritary video driver not a good idea"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by bigredcherokee on 2007-12-29
Ok I upgraded to 7.10 with no problems . It notified me that I was using a propritary ATI driver. 

I heasitated to disable it but then couriosity got the best of me.

I only boot to the prompt now. Help please.

Also my spelling suck I know.

---

### Post by Dark_Stang on 2007-12-29
Login in the terminal. Enter ```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through the process of setting up your xserver with the settings you want. The first step is choosing the driver, pick ati's driver right away. Then it's going to take you through setting up the keyboard, monitor size, monitor resolution, color depth, etc. After that enter ```
startx
``` to bring X back up. Or enter ```
sudo /etc/init.d/gdm start
``` to bring the gnome login manager up or ```
sudo /etc/init.d/kdm start
``` to bring up the kde login manager if you use kde.

---

