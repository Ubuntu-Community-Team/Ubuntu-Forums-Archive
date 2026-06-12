---
title: "Very primitive-looking xorg.conf file"
date: 2009-03-09
forum: Hardware
---

### Post by theresonant on 2009-03-09
Hi all!

I looked into my xorg.conf file, and it only contains this:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I mean ONLY this, except the comments. This is the version dexconf writes. I think my graphics card isn't working very well because of it (special effects go slow if many windows are open, especially 3d Windows for the cube). I am certain my graphics card would perform much better than that (I'm dualbooting with Windows XP, and games run very well). It's an Intel 945GM Express, inside a HP 530 laptop. I think xorg.conf should look like the intel driver is selected... Should I edit it manually?

Running Ubuntu Intrepid on 32 bits...

---

### Post by issih on 2009-03-09
xorg.conf files are usually a LOT less complicated than they used to be. That is to do with the newer versions of X rather than anything else.

Don't actually know whether your graphics driver should be in there off the top of my head, but a file that small isn't unusual these days.

Hope that helps

---

### Post by theresonant on 2009-03-09
Hm... I was still expecting to see something like 

```

Driver     "intel"

```

somewhere. Anyway, I added it, and also tried with Driver  "i810" under Device, but there were absolutely no changes. I'd really like to see my laptop going that fast in Ubuntu too. That is, the graphics, especially 3D. Processing and overall desktop experience is waaay faster than in Windows.

---

### Post by karlr42 on 2009-03-09
The xorg.conf file is nowhere near as important as it used to be- most guides you might find online about editing it are now out of date for 8.10.

---

### Post by theresonant on 2009-03-09
Then what should be the way to select the driver for my graphics card? In Hardy Heron there was a dialog-based utility for setting resolutions and selecting graphics cards. Which is gone in Intrepid. Anyway, I don't need GUI, so CLI is ok too. I just don't know any way to set it :)

---

### Post by haiku88 on 2009-03-09
do a search, there are many threads on this card, intel drivers, and xorg.conf....had to modify my own xorg to get my display right, but had provlems that are unique to Sony all-in-ones

---

