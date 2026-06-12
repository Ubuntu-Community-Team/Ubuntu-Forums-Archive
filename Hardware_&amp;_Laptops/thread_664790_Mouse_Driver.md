---
title: "Mouse Driver"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by Rexfordg on 2008-01-11
Hi. I have issues with my mice with Ubuntu. What happens is that the mouse works when it is connected to the PC while booting. About 10-20 minutes later when I am working, the mouse suddenly freezes up and stops working. I then disconnected the mouse but when I reconnected, it didn't even respond. I have done this with other brands of mice but ended up with the same results. I am suspecting that it may be the mouse driver because I did not have this issue happen when I had windows previously on this computer. 

Please layout some tips to get my mouse working, Thanks           -Rex

---

### Post by Yellow Pasque on 2008-01-11
What kind of connection do your mice have (USB, PS/2, serial)? Generally, your mouse shouldn't need a special driver. Paste the mouse section from your /etc/X11/xorg.conf file. It looks like the following:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

---

