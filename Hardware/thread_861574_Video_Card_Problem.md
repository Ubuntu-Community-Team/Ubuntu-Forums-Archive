---
title: "Video Card Problem"
date: 2008-07-16
forum: Hardware
---

### Post by Dave009 on 2008-07-16
I have a Nvidia GeForce 8600M GT on a Dell Inspiron 1520, and my video card is not being recognized. I have the proprietary drivers enabled, but its not still recognized. I tried removing all previous Nvidia drivers and reinstalling the new one again but to no avail. How can I fix this?

---

### Post by brokenLockpick on 2008-07-16
Are you sure your card is unrecognized?

Try ```
lspci | grep vga
``` from the terminal

Or alternately look in your xorg.conf file

path is /etc/X11/xorg.conf

---

### Post by Dave009 on 2008-07-18
```
lspci | grep vga
```

This command returns a blank line. In xorg.conf, this is the only entry under video devices:

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection
```

Whenever I boot up Ubuntu, I get a message telling me that my video card could not be detected, with options to configure, shut down or continue. This has happened ever since I upgraded from Gutsy to Hardy. Perhaps this time I didn't install the driver properly? Is there a recommended method for this?

---

### Post by StormPCs on 2008-07-18
Are you running 4GB RAM?

---

### Post by Dave009 on 2008-07-18
No, only 2 gigs. I also tried it with Envy last night, and to no solution; Envy was able to correctly identify my graphics card, installed patches/drivers without problems, but on reboot, the same error message and scenario.

---

### Post by brokenLockpick on 2008-07-18
I've only installed ubuntu on my desktop, rather than on a laptop. My hardware was just aweful as far as being recognized automatically, I had to do alot of manual editing to the xorg.conf file I've becom somewhat familiar with how it works, but I'm sure there are others on the board that are much more well versed in it. Maybe if you posted the whole xorg.conf file either myself or someone else might be able to notice a problem in it.

---

### Post by Dave009 on 2008-07-21
just an update and a reference for anyone with this problem later on, i did a fresh install of hardy and my problem was gone.

---

