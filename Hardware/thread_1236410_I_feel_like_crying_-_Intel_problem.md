---
title: "I feel like crying - Intel problem"
date: 2009-08-10
forum: Hardware
---

### Post by ohlookitskyle on 2009-08-10
Just before you read on you should know that I've installed Ubuntu using the exact same disc on the exact same laptop and the graphics have been working perfectly out of the box.

I have just reinstalled Ubuntu and the highest resolution I can get is  1024x768 on either of my screens (laptop LCD and external LCD). Before though I have been able to get 1280x800 (I think) on my laptop screen and 1440x900 on my other monitor.

I'm not that used to ubuntu yet (I know basics) and sorry about my sucky English skills.

Any help appreciated.

---

### Post by wojox on 2009-08-10
Is your driver activated? System > Admin > Hardware Drivers

---

### Post by ohlookitskyle on 2009-08-10
The box is empty. It says that there is no proprietary drivers in use on this system.

---

### Post by cascade9 on 2009-08-10
All the Intel video drivers that ubuntu installs are not proprietary in my (limited) experience. Try checking your xorg.conf to make sure its not limited to 1024x768.

---

### Post by tgalati4 on 2009-08-10
In a terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by ohlookitskyle on 2009-08-10
That's worked great, tgalati4 thanks!  +hug

---

### Post by tgalati4 on 2009-08-10
Keep that in your notebook.  Most programs can be reconfigured with dpkg-reconfigure.  Xorg needs it more frequently.

---

