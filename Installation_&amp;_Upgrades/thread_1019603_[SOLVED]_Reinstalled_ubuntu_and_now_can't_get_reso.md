---
title: "[SOLVED] Reinstalled ubuntu and now can't get resolution right"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by nlindz2065 on 2008-12-23
Hello, I reinstalled ubuntu last night and now I can not get my resolution right.  It only gives me two low options like 640x480 and 800x600 or something like that.  I need 1200x700 more or less.  Is there a way to correct this without having to reinstall again?

---

### Post by taurus on 2008-12-23
What graphic card do you have and have you looked in System -> Administration -> Hardware Drivers to see if there is a driver for your graphic card?

---

### Post by nlindz2065 on 2008-12-23
How do I tell what graphics card I have?  Also, I went to System - Admin - hardware drivers and it says that there are no proprietary drivers in use on my system.  There is nothing there?

---

### Post by taurus on 2008-12-23
```
lspci | grep VGA
```
Sounds like you have one of those Intel onboard graphic controllers.

---

### Post by nlindz2065 on 2008-12-23
nefertari@nefertari-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

I guess this is my graphics card?

---

