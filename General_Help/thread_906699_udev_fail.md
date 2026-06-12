---
title: "udev fail?"
date: 2008-08-31
forum: General Help
---

### Post by guttersnipe on 2008-08-31
Hello,

I recently purchased a usb mouse for my laptop, but when I plug it in, it seemingly does nothing.

The mouse itself is getting power (it's optical). I've verified that it's not a hardware issue as it works in a live-cd environment (Backtrack).

Upon further investigation, I've found that my laptop also cannot mount usb flash drives.  It doesn't do it automatically, nor do the devices show up in `/dev/disk/by-*` or in `lsusb`

I'm fairly certain that this was not an issue when I first installed Ubuntu on my laptop, so I'm betting the issue came about during an upgrade or a configuration change--somewhere.

Here's some additional info:

Model: HP Pavilion tx1000z
```
# uname -a
Linux trinity 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```
```
# cat /etc/issue
Ubuntu 8.04.1 \n \l
```
```
# lsusb
Bus 001 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 004: ID 0c45:62c0 Microdia 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000
```  



Any help will be greatly appreciated.

---

### Post by fragos on 2008-09-01
I see your not running the latest version of Linux supplied by the Ubuntu update manager. Current is 2.6.24-19-generic. I run a Wacom tablet, USB mouse and a USB touchpad and they all work interchagably. The mouse prtion of my /etc/X11/xorg.conf follows:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Perhaps if you made changes to xorg.conf you may have created the problem.

---

