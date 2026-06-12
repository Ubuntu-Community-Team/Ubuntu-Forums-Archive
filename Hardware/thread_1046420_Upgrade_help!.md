---
title: "Upgrade help!"
date: 2009-01-21
forum: Hardware
---

### Post by cheeseburgerman1 on 2009-01-21
Hi i am upgrading my processor, graphics card, and ram tomorrow.
current specs.
amd 64 athlong x2 2.0 ghz
1gb ram ddr2 4200 shared with onboard graphics card
Nvidia 6150le On board graphics card utilizing 256 mbs system mem

Specs after upgrades.
amd athlon 64 x2 2.9 ghz
4gb ram ddr 5300 mhz
EVGA GeForce 8500 GT 1GB PCIe w/Dual Link DVI
Pctuner card.
Upgraded cpu fan and power supply.

I was just wondering if there were any problems i might come up against when installing this or if there is a certain way i might want to go about it?

---

### Post by cheeseburgerman1 on 2009-01-21
please any thoughts?

---

### Post by howefield on 2009-01-21
Looks fine although you might want to check the tv tuner for compatibility to ensure a smooth install.

If you use 32 bit you may not see all of your 4 gig of ram, you would need to use 64 bit version, or the PAE enabled 32 bit kernel.

---

### Post by lswest on 2009-01-21
set your graphic driver to VESA before replacing the gfx card (e.g. disable any other drivers you installed by editing your xorg.conf file and changing the driver from nvidia to vesa).  Then, after you replace the card, re-install the drivers (otherwise you may face issues).

Other than that it should be fine.

---

### Post by cheeseburgerman1 on 2009-01-21
ahh thanks for the tip on setting to vesa. and one more tidbit that could help me out greatly would be whether i have to reformat a whole drive to switch to 64 bit, or just the partition the linux is installed on?

---

### Post by howefield on 2009-01-21
> **cheeseburgerman1 said:**
> ahh thanks for the tip on setting to vesa. and one more tidbit that could help me out greatly would be whether i have to reformat a whole drive to switch to 64 bit, or just the partition the linux is installed on?

You are not completely clear here, do you mean you have other operating systems on your disk or something else ?

---

### Post by cheeseburgerman1 on 2009-01-22
yes. i have vista 32 bit also installed on the drive along with a recovery partition for vista.

---

### Post by cheeseburgerman1 on 2009-01-22
Also, ummm apparently i need a little help either finding the correct version of xorg.conf or i dont actually know what i should be editing in the file. also, i have several xorg.conf files with numbers appended to the end, but this is the readout of the orginal xorg.conf

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
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

---

### Post by cheeseburgerman1 on 2009-01-22
Nevermind, i figured it out. my screen has been all uglified and enlarged.

---

