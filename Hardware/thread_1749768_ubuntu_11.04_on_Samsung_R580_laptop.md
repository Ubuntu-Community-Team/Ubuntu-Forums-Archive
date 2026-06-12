---
title: "ubuntu 11.04 on Samsung R580 laptop"
date: 2011-05-04
forum: Hardware
---

### Post by dsmex on 2011-05-04
Hi,

I'm posting my experiences with ubuntu and kubuntu 11.04 on my Samsung R580 laptop along with a few questions. Hopefully this will be of use for other people. 



**Kubuntu 11.04 - Clean install**
- Bug in "Hardware Drivers" tool. Says "NVIDIA binary driver is activated but not in use". The same message was shown independent of which driver was installed.
- Critical bug in KDE/NVIDIA causes system to freeze every now and then. Especially resizing Konsole window would trigger this. Had to power off computer and restart every time. 



**Ubuntu 11.04 - Clean install**
Works mostly out of the box. A few hacks are needed.

Install NVIDIA driver (from Additional Drivers dialog)

Wireless internet was slow and unreliable initially. Some web pages would load quickly, others slowly and again others would never stop loading.

This fix (found on other forums) solves the problem completely:
Create the file:
  /etc/modprobe.d/ath9k.conf

With the line:
  options ath9k nohwcrypt=1



Changing screen brightness using the power applet doesn't work initially.

To the file:
  /etc/X11/xorg.conf
Add the following line in the Device section:
  Option "RegistryDwords" "EnableBrightnessControl=1" 


Reboot the computer to see the effect of the changes.


I haven't tested everything, but at least the following works fine:
- Wireless internet
- Sleep/suspend
- Sound input/output
- Graphic card
- Hotkeys (Fn) for volume, screen brightness, disable touchpad


A few things that don't work yet:
- Hotkey to switch between laptop screen and external monitor (Fn+F4). Using "NVIDIA settings" dialog works, but it's a bit more cumbersome.
- Multi-touch gestures for touch pad. 


If anybody has simple fixes for these issues, please let me know.

---

### Post by Azrael84 on 2013-01-24
I'm finding this laptop incredibly slow running under Ubuntu 12.04, it takes an age to boot up then the login screen will hang after just entering the username, before even prompting for the password, the desktop and icons also take a few minutes to load. It is also prone to crashing it seems. This is even after a fresh install of the OS so I'm not sure what is causing it to be sooo slow. I use a Dell Inspiron 1764 running Ubuntu 12.04 as my main laptop and it seems infinitely faster ...I know the 1764 has an i5 vs the R580's i3, but I wouldn’t imagine that to be what's really making the difference.

---

