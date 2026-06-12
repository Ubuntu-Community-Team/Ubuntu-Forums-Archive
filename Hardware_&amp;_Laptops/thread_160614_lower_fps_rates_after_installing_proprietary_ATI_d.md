---
title: "lower fps rates after installing proprietary ATI driver"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by fubar0 on 2006-04-15
Hello, 

I am running Breezy on a DELL Inspiron 6000 containing a Mobility Radeon X300 128 MB. 
After the initial installation of Breezy, ```
glxgears -printfps
``` only indicated  around 630 fps, so i decided to install the proprietary ATI drivers after this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)
The result was surprising: 130 fps!

I tried out various settings with ```
dpkg-reconfigure xserver-xorg
```, with no effect.

Can anyone help me on this?

---

### Post by fubar0 on 2006-04-15
What I forgot:
```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```seeing this, one would say that the driver is not (properly) installed.

On the other hand side, after installation,```
dpkg-reconfigure xserver-xorg
``` recognizes the following device, when I select "auto" device detection (from /etc/X11/xorg.conf):
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by fubar0 on 2006-04-16
I found the following error in /var/log/Xorg.0.log:

[INDENT](EE) fglrx(0): Hardware already been locked.[/INDENT]

Does anyone have an idea how to fix this?

---

### Post by Miguel on 2006-04-17
Hi fubar,

What exactly have you done? I don't know what on this guide have you done. First of all, I would uninstall everything fglrx related, and then attempt to recover the state. It will probably suffice by doing a sudo dpkg-reconfigure xserver-xorg and selecting either the ati or radeon drivers (for your card they are effectively identical).

So, can you recover your system to the previous state? Let's work on it step by step. Ah!, by the way, what do you prefer? Breezy drivers (easy) or latest drivers (harder, slightly more performance)?

---

