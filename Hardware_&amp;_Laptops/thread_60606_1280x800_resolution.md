---
title: "1280x800 resolution"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by lozzd on 2005-08-28
Hello,

I have an Acer TravelMate 3002WTMi, which after reading a couple of threads have learned hardly works with Ubuntu, or any linux, thanks to the way the hardware works.

Anyway, to solve this problem, I'm running in a VirtualPC (MS 2004) which is working fine, apart from I'd quite like to run it full screen in the laptops native resolution (1280x800). 
To do this when using the actual graphics card, you could use "855resolution", but because this a VirtualPC that does not work. 
I have tried altering the xorg.conf config file to allow only 1280x800 but Ubuntu won't show this. instead I'm using a very stretched 1024x768.
Any ideas?

Thanks
Laurie

---

### Post by lozzd on 2005-08-28
[QUOTE=lozzd]Hello,

I have an Acer TravelMate 3002WTMi, which after reading a couple of threads have learned hardly works with Ubuntu, or any linux, thanks to the way the hardware works.

Anyway, to solve this problem, I'm running in a VirtualPC (MS 2004) which is working fine, apart from I'd quite like to run it full screen in the laptops native resolution (1280x800). 
To do this when using the actual graphics card, you could use "855resolution", but because this a VirtualPC that does not work. 
I have tried altering the xorg.conf config file to allow only 1280x800 but Ubuntu won't show this. instead I'm using a very stretched 1024x768.
Any ideas?

Thanks
Laurie[/QUOTE]
 Its really annoying me now, i've tried so much. I've looked in my log file and next to the mode it says "bad mode clock/interlace/doublescan". What does this mean?

It even comes up with the mode at first, and then goes back to 1024x768 again (very quickly)

---

### Post by lozzd on 2005-08-29
How hard is it to override X?! It's not like i'm gonna damage a virtual monitor, so it doesn't matter that much. Someone must know how to stop it caring? I've now spent hours googling trying to find an answer!

Thanks

---

### Post by TheSavage on 2005-08-29
Here's my xorg.conf file.  I hope this will help you.

---

### Post by sneax on 2005-08-29
All I can think of is this:
Did you set your 'maxvertkhz' and 'maxhorhz' or something like that in your xorg.conf? I mean this:

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Philips CM0200 (14B)"
	[b]HorizSync    31.0 - 48.0
	VertRefresh  50.0 - 100.0[/b]
	Option	    "dpms"
EndSection

(just the bold, the rest is example) Adding those 2 lines in my xorg.conf enabled me to do all resolutions instead of the only 2 that xorg detected upon install.

---

### Post by lozzd on 2005-08-30
[QUOTE=TheSavage]Here's my xorg.conf file.  I hope this will help you.[/QUOTE]

Thats the exact modeline I had...


[QUOTE=sneax]All I can think of is this:
Did you set your 'maxvertkhz' and 'maxhorhz' or something like that in your xorg.conf? I mean this:[/QUOTE]

Yep tried that, doesn't work. 

Thanks anyway you guys.

---

### Post by sneax on 2005-08-30
You are running a virtual pc (I don't realy know what it is) but maybe that's the problem? Does that virtual pc thing allow resolutions up to 1280*800? I'm sure you already though of all that but it's just an idea :)

---

### Post by lozzd on 2005-08-30
[QUOTE=sneax]You are running a virtual pc (I don't realy know what it is) but maybe that's the problem? Does that virtual pc thing allow resolutions up to 1280*800? I'm sure you already though of all that but it's just an idea :)[/QUOTE]

Well it should do but obviously isn't going to work. 
So I'm just about to try VMWare instead! :P I'll let you know.

---

### Post by lozzd on 2005-08-30
WMWare has fixed the problem perfectly. Ubuntu worked first time at 1280x800 in WMWare, and I'm now typing on it, quick, beautiful, but still full laptop support. 
Another good reason to abadon Microsoft products. 

Thanks to everyone who offered their help.

Laurie

---

### Post by EstevaoSoares on 2006-02-08
Hi there.. 

For those users of ATI Radeon Xpress 200M that are in pain with the resolution, the new ATI driver already covers that 1280x800. So sweet! 

Just Install (look in this forum for How to install the last ATI driver) and voilá! Its there! 


Well, a litle out of topic but good luck for everyone.

---

