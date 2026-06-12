---
title: "Display problems after upgrade to 8.10"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by PaulHuffman on 2009-05-25
I have an old Gateway g6 with a VGA monitor, an EV700, that was running 8.04 fine, but when I applied an upgrade to 8.10, the display has shimmering lettering and backgrounds. I went on and applied a 9.04 upgrade as well, but I have the same shimmering hard to read screen. Forgive the typos, but I can't always see what I'm typing.  Prefernences>Display indicates "Unknown monitor" but I haven't figured out what to do about it.

---

### Post by PaulHuffman on 2009-05-31
I played around with some differnet settings in xorg.conf, but hit error messages when I restarted. Couldn't get back to the desktop to rename my backup to restore previous settings. Eventually chose to create a new profile from one of the little pink screens, and that got me back to the desktop with the same problems as above. Isn't there a way to I escape to a non graphical console if I screw this up again?

Trying to run 9.04 32 bit.

Figured out that cntrl-alt-function key will get me to non graphic consoles. Now how to I get back?

---

### Post by PaulHuffman on 2009-05-31
I found some configuration settings for the EV700 and changed my xorg.conf to 

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30 - 70
	VertRefresh	50 - 120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection 	"Display"
		Modes	"1280x1024"
	EndSubSection
EndSection

```

At least it boots now, but it doesn't fix my display problem.

Noted that when the system boots, I see a message "BIOS fails cutoff (1998).  Is this system too old to run 8.10 or 9.04?

---

