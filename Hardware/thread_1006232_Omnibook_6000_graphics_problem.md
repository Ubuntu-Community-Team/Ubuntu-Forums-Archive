---
title: "Omnibook 6000 graphics problem"
date: 2008-12-09
forum: Hardware
---

### Post by Freiksenet on 2008-12-09
Hello!

Ubuntu 8.10

Spent lots of time trying to make my HP Omnibook 6000 run properly - it always wants me to reset to VESA driver with 640x480 resolution and bad refresh rate.

The main problem is that I can't tell which video card I have - all specifications of Omnibook shows that I should have ATI, but grep show that I have intel card. Both drives don't work though - when I try to use "intel" in logs I see that "Nothing is connected to VGA output" and then it resets, and when I use "ati" it says "No drivers found". :confused:

I wonder what can I do to finally make it work, I don't need any 3d capability, just normal resolution and refresh rate.

Thanks a lot beforehand.

UPD:

The actual label was pretty hard to decipher, but now I think it is not Omnibook 6000, but Omnibook xt6050. It had Omnibook 6000 on the bottom, so it confused me. So the actual graphic card is Intel. The problem persists though, it seems that intel driver cannot see laptop screen connected. It used to search through VGA output, I though disabling it in xorg.conf would help, but it didnt. Now it just says "No outputs definitely connected, trying again", and then unloads.

---

### Post by nanooq on 2009-03-12
Hi,

I just solved this problem on my Omnibook 6200 (finally, after weeks and weeks). It's probably the same on the Omnibook 6000 as the symptoms are the same.

The strange things was that it used to work fine in a previous 8.04 installation.

However, the key is probably to disable DRI...for what it's worth.

Here is a (for me) working xorg.conf that should enable you to boot into the ATI resolutions (and then enable you to switch to higher resolutions thru the GUI):

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	
	Option	"DRI"	"off"

EndSection

Section "Module"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

```

If you want to you can det the DefaultDepth to 24 and the Modes to "1400x1050".

I will probably try out some more options for fine tuning as the Omnibook is "really busy" with Ubuntu and to get the most out of it.

hth,
n

---

