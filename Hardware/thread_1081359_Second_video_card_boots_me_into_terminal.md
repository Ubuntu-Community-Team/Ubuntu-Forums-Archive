---
title: "Second video card boots me into terminal"
date: 2009-02-26
forum: Hardware
---

### Post by houseonfire on 2009-02-26
I have two video cards, each ATI X1650 Pro. I have a virtual machine of XP installed so I can play 2142.
My second card was being used for another computer, but is not needed anymore. So I plugged it into my computer.
Odd thing is, when the card is plugged in, the ubuntu loading bar loads, and then I go to the terminal. I unplugged it and I booted right into ubnutu no problem.
Does anyone have a solution for this? I would really like the physics rendering for my games, and my Python projects.

Thanks guys, and love th OS.

---

### Post by houseonfire on 2009-02-26
help please

---

### Post by houseonfire on 2009-02-27
bump

---

### Post by markbuntu on 2009-02-27
The latest driver from ati has built in support for multiple gpus. Otherwise you would need to edit your xorg.conf file.

---

### Post by houseonfire on 2009-02-28
I have the latest driver from ATI.

xorg.conf::
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


```

---

### Post by markbuntu on 2009-02-28
You need to use the catalyst control center that comes with the driver. It is in your menus somewhere.

---

