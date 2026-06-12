---
title: "Fatal error - No Screen Found on a Radeon x700"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by Chris107 on 2005-07-24
I'm trying to run the AMD64 version of Ubuntu on my Athlon 64 3200+ using an ATI Radeon x700 Pro

I first tried the Live CD and I got it to work using ATI drivers.

Now I installed and I get

```
Fatal error 
no screen found
```

I was told changing the driver to radeon fixed this but I don't have radeon as a choice and I can't run gedit because it says it can't be displayed.  Anyone have any ideas?

---

### Post by huwshimi on 2005-07-27
Hi, I'm no expert but you could try the following.

In a terminal type...

```
sudo nano /etc/X11/xorg.conf
```
Scroll down to you get to a section something like this
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 Pro"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```
And change the driver to radeon...
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 Pro"
	Driver		**"radeon"**
	BusID		"PCI:1:0:0"
EndSection
```
then save(ctrl+o), exit(ctrl+x) and startx

Good luck with it.

---

