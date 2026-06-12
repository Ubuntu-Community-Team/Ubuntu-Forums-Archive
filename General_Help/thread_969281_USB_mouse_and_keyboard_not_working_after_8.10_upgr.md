---
title: "USB mouse and keyboard not working after 8.10 upgrade"
date: 2008-11-03
forum: General Help
---

### Post by philosophia on 2008-11-03
Hardware: Dell Optiplex GX620, usb keyboard and mouse running through an OmniView usb kvm switch

My usb mouse and keyboard are not working after upgrading from 8.04 to 8.10.  Ubuntu 'loading' bar during bootup looks weird now - it's cut off and split into two bars.  I also have some error messages during bootup

```
usb device not accepting address 13, error -71
unable to enumerate usb device on port 5
...
unable to set system time to: ...

```

I've tried running dpkg-reconfigure to reset xorg.conf, no change.  Any suggestions?

---

### Post by philosophia on 2008-11-07
Bump.  I've tried plugging the mouse and keyboard directly into the computer, bypassing the hub - they are still not being detected, although the boot error goes away.  Anyone?

---

### Post by jdenkaat on 2008-11-08
Intrepid has a new way to configure mouse & keyboard. The easiest way to get your mouse working is to disable this feature. 

edit /etc/X11/xorg.conf

put the following at the start


Section "ServerFlags"
Option         "AutoAddDevices" "false"
EndSection

Uncomment all your mouse and keyboard configurations they will have the heading > commented out by update-manager, HAL is now used, 

mine are

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

save and reboot

---

### Post by philosophia on 2008-11-10
I tried this, I get the same errors when I reboot.  I tried plugging my usb mouse and keyboard directly into the  computer, they still don't work.  I'm attaching my current xorg.conf with the mouse and keyboard uncommented and the ServerFlags section.

Should I reinstall?  Seems a waste if this is just an xorg problem.


> **jdenkaat said:**
> Intrepid has a new way to configure mouse & keyboard. The easiest way to get your mouse working is to disable this feature. 

edit /etc/X11/xorg.conf

put the following at the start


Section "ServerFlags"
Option         "AutoAddDevices" "false"
EndSection

Uncomment all your mouse and keyboard configurations they will have the heading , 

mine are

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

save and reboot

---

### Post by philosophia on 2008-11-12
bump?

---

### Post by philosophia on 2008-11-12
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840)

this fixed my problem

---

