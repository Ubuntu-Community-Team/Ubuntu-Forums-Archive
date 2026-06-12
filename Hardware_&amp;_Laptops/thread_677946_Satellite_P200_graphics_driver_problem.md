---
title: "Satellite P200 graphics driver problem"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by ancientrustic on 2008-01-25
I have Kubuntu Gutsy on a Toshiba Satellite P200. The graphics card is a Radeon HD2400. My problem is that I cannot get the native resolution of 1440x900 and I cannot activate desktop effects. I've ticked all the boxes in system settings but they do not work. I've tried various tweaks to xorg.conf which usually results in a fail to boot and I have to switch the settings back. Can someone tell me how to install the correct driver and get it working?

---

### Post by wyvvie on 2008-02-02
I have the exact same model :)

You have to use the new RadeonHD driver - the catalyst one will only do a res of '1152xsomething'. There have been reports of people getting the fglrx driver to work in [this thread]("http://ubuntuforums.org/showthread.php?t=570391&highlight=radeonhd&page=1") but I haven't had any luck with anything other than the radeonhd.

To get the new driver to work, you should have most Device/Monitor/Screen sections left blank in the xorg.conf file as the driver will automatically find them itself, the relevant parts are here:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"radeonhd"
	VendorName	"ATI Technologies Inc"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection
```

This curently supports composite effects (in XFCE4 all the transparency and shadows are working correctly) but don't expect a high score in glxgears (~960). I have the full 1440x900 res too :3

I'm not currently using Ubuntu, so I don't know if the driver is in the repositories, but if not then try compiling from source :)

---

