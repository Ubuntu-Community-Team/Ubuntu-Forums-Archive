---
title: "Problems with nvidia propietary drivers"
date: 2009-12-22
forum: Hardware
---

### Post by Dynux on 2009-12-22
Hi all,
I've an Asus laptot model K50IN with this Nvidia graphic card: GeForce g102m.
I've installed Ubuntu 9.10 64bit version.
I tried to install the proprietary drivers ( 185.xx and 190.xx ) but at the reboot the screen was divided into six smaller screens.
I've asked a lot but i have no solution :( .
Please help me, these are the data that I give you to try to solve the problem ( the result of the command "uname -a" and the xorg.conf file ).
Sorry for my english i'm italian,
Bye Dynux.

---

### Post by realzippy on 2009-12-22
Open xorg.conf

**gksudo gedit /etc/X11/xorg.conf**

and insert this line:

*Option "ModeValidation" "NoTotalSizeCheck"*

in "Device" Section,like this:

[I]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "ModeValidation" "NoTotalSizeCheck"
EndSection[/I]


and restart X



from:
[http://www.nvnews.net/vbulletin/showthread.php?t=137379](http://www.nvnews.net/vbulletin/showthread.php?t=137379)

---

### Post by Dynux on 2009-12-22
I'm sorry but remains six screens :(

---

### Post by realzippy on 2009-12-22
Restarted X and xorg edited correctly?
...just asking,because it is a common solution for the "6screens" problem,e.g. here:
[http://ubuntuforums.org/showthread.php?t=1230528](http://ubuntuforums.org/showthread.php?t=1230528)


Have you run all system updates?
Install the newest (195.22) driver manually ...:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by Dynux on 2009-12-22
Yes, but i don't have tried the beta drivers 195.22.
There are 3 package, what package i have to download?

---

### Post by realzippy on 2009-12-22
[http://www.nvidia.com/object/linux_display_amd64_195.22.html](http://www.nvidia.com/object/linux_display_amd64_195.22.html)

---

### Post by Dynux on 2009-12-22
Still the same 6 screens :'(

---

### Post by realzippy on 2009-12-22
You could try :
[B]
sudo rm /etc/X11/xorg.conf[/B]

**sudo nvidia-xconfig**

then again insert device line.Restart X.
If no luck,you can  ask somebody for his working xorg.conf and which driver is used from this thread:

[http://ubuntuforums.org/showthread.php?t=1247196](http://ubuntuforums.org/showthread.php?t=1247196)

---

