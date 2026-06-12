---
title: "CLI help ( driver install in CLI )"
date: 2009-01-30
forum: Hardware
---

### Post by jenova_skill on 2009-01-30
On my last resort trying to fix my 3d GFX I've read a post to remove/ uninstall Drivers and reboot ubuntu to pick up the Driver's in hopes of it Picking up the right one automatically
Needless to say it didn't work and now im stuck in CLI booting up ubuntu with no drivers ( I am guessing ).

I try to start the GUI and It comes up with 

blahh blahh
(EE) VESA(0): No valid modes
(EE) Screen(s) Found, but none have usable configuration

Fatal sever error:
no screens found 
giving up

connection refused unable to connect to X sever


Can someone please help me with my problem... I assume i just need to manually install my GFX driver and it will fix the problem I have an ATI X1250. I've tried to use Envyng to install it (i have it installed on cpu)  
It says it fails to fetch from the server

---

### Post by taurus on 2009-01-30
Try to reconfigure your X server again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by jenova_skill on 2009-01-30
SOLVED

[http://ubuntuforums.org/archive/index.php/t-979379.html](http://ubuntuforums.org/archive/index.php/t-979379.html)

---

