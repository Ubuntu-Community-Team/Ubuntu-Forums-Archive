---
title: "Install on laptop - Acer Aspire 1350 - My display looks like backgammon"
date: 2005-11-09
forum: General Help
---

### Post by daller on 2005-11-09
Hi There,

Starting the Kubuntu install on my laptop, Acer Aspire 1350, the display looks like backgammon (a lot of zig zags...)

Is there a way to choose a laptop setting, to avoid this?

Kubuntu Breezy Badger

...I aborted the installation (hard off), after if think it stalled...

Now it starts great! (usplash looks very zaggy (a lot of blue lines!))

After this, KDE starts great, and seems to work!

Any idea on how to fix this?

---

### Post by daller on 2005-11-09
The install-part, can easily be fixed with this argument (at beginning of install)

linux vga=771

...About the KDE startup thing, I still didn't figure it out... (vertical stripes)

---

### Post by Thingymebob on 2006-08-15
I'm getting the same on my aspire 1350 during boot.

If you enter something like vga=791 in boot/grub/menu.lst then you get an invalid vga mode message.

If you enter something like vga=6 then at least you get a text boot. doesn't look as nice as the splash but at least you get see whats happenning.

I'm also having a problem with user switching, when the screen is blanked before switching it fails to restart, can here the login sounds etc but no display. I've seen a bundle of posts about similar things here and am still working through them to see which one works.

---

### Post by Thingymebob on 2006-08-15
Sorry - Double Post

---

### Post by Thingymebob on 2006-10-10
Works fine in 6.10, but user switching still ends up with black screen, Seems to problem with via driver, vesa driver works fine but is real slow.

---

### Post by Thingymebob on 2006-10-12
Adding :
Option "VBEModes" "True"
To the video card section in /etc/X11/xorg.conf gets user switching working properly

My display device section now looks like this:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
	VideoRam	64000
	Option		"UseFBDev"		"true"
	Option		"VBEModes"		"true"
EndSection

```

---

### Post by fragos on 2006-10-12
"lspci|grep VGA" will show you what video chip set you have.  I put Ubuntu on a different version of Acer Aspire with a wide screen.  It had an SIS chip set it wasn't automatically recognized by Linux.  In this case I edited /etc/X11/xorg.conf to change driver from "vesa" to "sis".  That driver would recognize the 1280x800 resolution after I told xorg.conf to use it.  I don't know anything specific about your laptop.

---

