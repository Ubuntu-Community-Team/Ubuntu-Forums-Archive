---
title: "GM45 Intel Graphics driver help needed"
date: 2009-02-23
forum: Hardware
---

### Post by storm1988 on 2009-02-23
I've been trying to get my girlfriend's laptop graphics drivers to load but im having no luck.

It is a Advent 5431.

Here is the lspci output of the graphic chip:
"Intel Corporation Mobile 4 series chipset Integrated Graphics Controller (rev 07)"

any help would be appreciated.

Storm

---

### Post by Squid Spectre on 2009-02-23
Hey, I have that same graphics card in my laptop. It took me a bit to get it working myself though I think mine was a problem realted to having both discerted and integrated graphics.

The trick is to make sure you have the following package installed:
     xserver-xorg-video-intel

Then make sure that your xorg.conf looks something like this:

```

...

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"intel"
EndSection

...

```

Check to make sure those two things are in play and check back in if there are still issues.

---

### Post by storm1988 on 2009-02-23
Thank you for the quick response.

We have tried reinstalling the package and the xorg.conf is the same as yours.

Storm

---

### Post by Squid Spectre on 2009-02-23
Hrm, try posting your xorg.conf for me to look at, and what are you trying to do that indicates its not working correctly?

---

### Post by storm1988 on 2009-02-24
Basically the resolution is set at 1024 when the screen can display higher resolutions and is set at 4:3 when the laptop is a wide screen.

I'm at college today till 8pm (GMT) so i cant upload it atm but i might be able to get my girlfriend to up load the info.

Storm

---

### Post by storm1988 on 2009-02-24
hey, this is storms girlfriend. this is my xorg.conf

> 
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"	
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

cheers

---

### Post by storm1988 on 2009-02-24
Anything?

The config file looks empty but my laptop has even less??? Mine is missing the intel line.

Storm

---

### Post by storm1988 on 2009-02-24
Is there a way of adding my own screen resolution the config??

Also i have a weird fault on both mine and hers laptops where the active 3D graphics run on top of anything else. I added a picture of glxgears on top of firefox.

Storm

---

### Post by storm1988 on 2009-02-25
I have fixed the fault in the pitcure now. it was compiz so i turned it off. Is there a way to alow me to use compiz without the bugs on 3d graphic programes??

Storm

---

