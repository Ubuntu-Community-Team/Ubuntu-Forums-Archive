---
title: "Ubuntu will no longer load after package installation?"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Linuxforme on 2009-02-22
Hello, I am new to Ubuntu. I tried to install drivers for my Geforce Video card. I did a command to install on Konsole and it said it installed the Nvidia 173 package and then it asked me to choose to restart. After the computer restarted, Ubuntu tries to load but fails and shows me a screen with a lot of diagnostics check screen with everything being ok. I have no idea what to do to get it to load Ubuntu? Please help me, thanks.
Linuxforme is online now Report Post   	Edit/Delete Message

---

### Post by frost151n on 2009-02-22
Hey, 
When I had driver problems I rebooted into recovery mode and there's an option like 'try to fix xserver' or something, and that usually removed the driver thus fixing the issue. 
You should probably wait for a second opinion though!!! Fidgiting with Xserver is tricky business.

---

### Post by Linuxforme on 2009-02-22
> **frost151n said:**
> Hey, 
When I had driver problems I rebooted into recovery mode and there's an option like 'try to fix xserver' or something, and that usually removed the driver thus fixing the issue. 
You should probably wait for a second opinion though!!! Fidgiting with Xserver is tricky business.

Thanks a bunch.  I did as you did and Ubuntu loaded perfect.  I am guessing the Nvidia kernel did not gel well??  Thanks again.:D

---

### Post by frost151n on 2009-02-23
You're welcome.
For the drivers try
1. From the Desktop press Ctrl+Alt+F2
2. Sign In
3. sudo killall gdm
4. sudo sh (full driver package name)

---

