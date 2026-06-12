---
title: "Black screen at startup on an Acer Aspire 3023"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by theophane on 2007-05-10
Hey folks, 
when I boot on Feisty, I get a black screen at startup, is there any way I could fix this ?
My laptop is an Acer Aspire 3023 with an X700 graphic card on it.

Cheers :)

---

### Post by Ken_Lewis81 on 2007-05-11
I have the same Radeon 200 Express chipset in my laptop and the same graphics card.  This issue's been raised in the bug tracker at [launchpad.net](launchpad.net) a couple of times.

To work around this, you need to add the line in bold and starred (but without the bold or stars) to /etc/X11/xorg.conf:
```
Section "Monitor"
	Identifier	"Generic Monitor"
*****     Option		"MonitorLayout" "LVDS, Auto" *****
	Option		"DPMS"
EndSection

```

I usually load up the LiveCD, press Ctrl-Alt-F1 to go to a console, and then add the missing bits to /etc/X11/xorg.conf (I also add "1280x800" to each 'Modes' line in the "Section "Screen" -> SubSection "Display" " for the native resolution of my panel.)  Then, having saved the changes, reload X by pressing Ctrl-Alt-Backspace, which should let you get the best out of your system.  Installing at this point will keep these changes.

Hope that helps,

Take care.
Ken.

---

