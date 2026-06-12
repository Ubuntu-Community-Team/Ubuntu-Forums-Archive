---
title: "P.I.T.A boot error"
date: 2008-08-26
forum: General Help
---

### Post by muzikoverdose on 2008-08-26
After doing a recent update, every time I boot my laptop (Fujitsu Lifebook N3520, I get the following

Undefined Video Mode Number 307 

with the option to pick one of 6 video modes (?) or to just wait. It will boot into Hardy, but i'd rather not have to have this error every time.  Any help is greatly appreciated.  Many thanks ;)

---

### Post by LateNiteTV on 2008-08-26
please post your xorg.conf

---

### Post by muzikoverdose on 2008-08-26
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by muzikoverdose on 2008-09-01
dont suppose you have any ideas?im completely stumped :)

---

### Post by plucky on 2008-09-01
> Undefined Video Mode Number 307 

I think this is because the video card is trying to run at an undefined resolution.To see what it will support,open a terminal and ```
sudo hwinfo --framebuffer
``` Post the output to the forum.

Video Mode No 307 is resolution 1280X1024

To try a lower resolution,you have to edit your **/boot/grub/menu.lst** and add the value vga=791 to the kernel line e.g
```
 kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=71029edc-eaee-4be4-a53c-89bb8e8ac780 ro quiet splash [color=blue]vga=791[/color] 
```

So ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst
```

Add the value **vga=791** and save.

Then ```
sudo update-initramfs -u
``` to generate a new initramfs file.

Reboot and see if that works.


Good Luck

---

### Post by Seeker84 on 2009-08-02
I hope you were able to solve your issue.

If not, try commenting out the vga value and see if that works.

---

