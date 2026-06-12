---
title: "Synaptic Touchpad Problems"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by Evil Blu Jedi on 2007-07-05
Hi,
I am running a dual-boot HP Laptop dv5000 series with XP and Ubuntu Feisty.  I am having problems with my synaptic touchpad acting erratically.  The cursor moves too fast sometimes, then it will lag and not move at all.  Also, I tried disabling the tapping to click feature under xorg.conf, but it re-enables itself after about a minute.  Additionally, I downloaded and installed GSynaptics and can get to the GUI, but modifying the settings from there has no effect.
Somebody please help me.  I am still new at Linux, so go easy on me.  I can post more info if needed.  Thanks!

---

### Post by Death_Sargent on 2007-07-05
sounds like your touchpad is failing.

---

### Post by Evil Blu Jedi on 2007-07-05
The touchpad still works fine under windows.  Thanks for the quick response, though.

---

### Post by geraldm on 2007-07-06
There is a manpage on synaptic.  Any part can be set if can get into its
configuration.  Please try chasing it down through the manpage.

---

### Post by Evil Blu Jedi on 2007-07-06
Thanks, I seem to have disabled the tapping feature, but every so often, the cursor stops for about 3 seconds and will not move.  Is this normal, or is something wrong?

---

### Post by zabien1970 on 2007-07-07
I've had the same problem on a DELL Inspiron 6000, I think it may have to do with me constantly having my finger on the touchpad, not sure of the proper terminology but I know the CPU is constantantly processing things one at a time and if the touchpad is sending info and something else sends something that has priority it will store this to be processed later, then try to catch up, I try not to rest my finger on the touchpad constantly, even though it is convenient and this seems to help. Although I'm probably wrong it seems to make sense and if there is a way possibly to slow down the speed of the (I think its the IRQ's) it should run more smooth.
 Once again I'm probably wrong but if this is the solution maybe someone can help us both out with this problem.

---

### Post by Evil Blu Jedi on 2007-07-07
I was wrong about disabling the tapping "feature."  Even though it was off since my last post, it has somehow enabled itself again without any input from me.  I am including its entry from the xorg.conf file.  Did I do anything wrong?

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
	Option		"MaxTapTime"		"0"
	Option		"TouchpadOff"		"2"
EndSection

```

---

### Post by Evil Blu Jedi on 2007-07-15
I think I found what the problem was.  Somehow my wireless card drivers were the cause.  I have the infamous Broadcom chipset and had used fwcutter to get it working.  It was after that that the touchpad was erratic.  I, instead, installed the wireless drivers using ndswrapper, and now it works fine.

---

### Post by commike37 on 2007-07-27
Hey, I have the same problem disabling tapping, and I use fwcutter with an evil Broadcom chip, too.  I wonder where a bug report could be filed about this.

---

