---
title: "Help to configure Logitech mouse..."
date: 2009-04-06
forum: Hardware
---

### Post by BluBird302 on 2009-04-06
Hey guys, I am a newbie to Ubuntu 8.10 and so far I am liking it (long time windoz user).  I seem to have a problem with trying to figure out how to configure my LX3 Logitech optical mouse, of course I tried their website but no Linux drivers.  I have read several posts on here but still cannot get it figured out.  Everything on the mouse seems to work except for the left and right slide buttons on the scroll wheel.  I have read to check the xorg.conf file for the imput and edit, but on my file it doesn't show the input for the mouse.  I have tried imwheel but not really sure how to set that up either, and also ran the sudo dpkg-reconfigure -phigh xserver-xorg command and the results below is what I have.  I mainly want to get these buttons to work for Firefox 3, to forward and go back through the pages, but have been unsuccessful so far.  I'm not sure what information you guys need so please ask and I will do the best I can, is there something I'm missing here?


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

---

### Post by BluBird302 on 2009-04-07
I hate to double post but surely you guys may have some idea of how to configure my mouse, or atleast have some ideas, I would greatly appreciate anything.

---

