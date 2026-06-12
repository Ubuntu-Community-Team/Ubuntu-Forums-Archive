---
title: "Mouse and Keyboard dead in Jaunty"
date: 2009-06-22
forum: Hardware
---

### Post by schmolch on 2009-06-22
I installed Jaunty on a Thinkpad X22 and neither the Mouse nor Keyboard work in X.
I can switch to console and there the keyboard works but thats all.
No reaction in X whatsoever.
And im talking about the integrated keyboard and mouse of the laptop, not something external.

WTF?

---

### Post by terdon on 2009-06-23
Try adding these lines to your /etc/X11/xorg.conf file:

```
Section "InputDevice"
	Identifier	"Keyboard"
	Driver	"thinkpad"
EndSection

```

Then restart X. 

As for the mouse, are you talking about the trackpoint, the trackpad or the ultranav? None of them work? Can you try plugging in an external mouse? Everything works fine on my T400.

Or you can try and force X to autodetect them again:```

sudo dpkg-reconfigure -phigh xserver-xorg

```

CAUTION: this last command will overwrite any changes you may have made to your xorg.conf file.

---

