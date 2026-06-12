---
title: "Ibex - keyboard configuration"
date: 2008-11-08
forum: Hardware
---

### Post by lvshankar on 2008-11-08
Hi,

I did a fresh install of ibex from the alternate cd. my sata hard disk requires me to set the controller as AHCI in BIOS and boot with pci=nomsi.

However, the screen froze just before the login page and I couldnt do anything but reset or power down my box.
I thought the problem might be with xorg.conf and tried to view it via recovery mode (single). the file was empty.

I then used dapper live and copied the xorg.conf file from it to ibexs copy. This works fine for me, however my keyboard now doesnt throw the single/double quote when the key is pressed. instead i get the grave accent like this é (single quotes) or ë (double quotes).:confused:

Here is my xorg.conf: [http://paste.ubuntu.com/69232/](http://paste.ubuntu.com/69232/)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

my system config is as follows:
a8v-mx mobo (VIA K8M800 + VT8251)
amd athlon 64-bit 3000+
80 gb sata
101 us intl keyboard (converted to ps/2 port)
ibex 32 bit

---

