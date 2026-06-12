---
title: "Wacom stylus stops working in login screen, works otherwise"
date: 2009-05-03
forum: Hardware
---

### Post by KVirtanen on 2009-05-03
Hi there,

I've got an HP Compaq TC1100 Wacom 'penabled' slate tablet PC with Ubuntu 9.04 installed and have got pretty much *everything* to work just by skimming through the various tutorials around the net. Just now I got the on-screen keyboard (onBoard) to work on the login screen, but for some reason the stylus doesn't respond. The trackpoint mouse in the detachable keyboard works though.

The stylus works after logging in, but not after I log off again, basically it works during the Gnome session. I'm guessing the Xorg server is restarted between the session and logging off (I'm not exactly a Linux expert, but an experienced hobbyist :) ), but does it use another xorg.conf file or something? 

I didn't notice this behaviour before because I had automatic login on. I'm more than happy to provide any required attachment config files, but I'm writing this on another computer that I'm updating to Jaunty at the moment and don't have access to the tablet PC.

Maybe someone could point me in the right direction or provide some helpful insight as to how things differ between the Gnome session and the login screen in regards of how input devices and such are detected.

---

### Post by KVirtanen on 2009-05-03
*sigh..* Nevermind, it started working for some reason. I had a problem with a long blackout time between the boot splash and the login screen, but I added a few lines to xorg.conf to disable the autodetecting of input devices (a problem with HAL it seemed).

I wonder if that did the trick. The lines were simply:

```
Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection
```

---

