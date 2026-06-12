---
title: "External monitor, Intel VGA, jaggy scroll"
date: 2010-01-13
forum: Hardware
---

### Post by kosen on 2010-01-13
Hi there!

Searched through the forums, but did not find solution.

_Scenario:_
- using **Ubuntu 9.04**
- FuSi **Amilo netbook** with small display, native resolution: 1024x600
- using external monitor, which is a 17 inch LCD, capable of outputting 1280x1024.
- **lshw** display output:
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

I'm not sure, but I believe I downloaded the driver from Intel as I had problems with the provided one after upgrading to 9.04.

_Aim:_
- use both monitors at their native resolutions

So far, I've achieved flawless operation in 1024x600 + 1024x768 config (Ubuntu sets this as default resolution). There was no option for higher resolutios in the combo box (display config), but I've managed to use the external display in native resolution by modifying xorg.conf:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1024
	EndSubSection
EndSection

However the movement on the external display is jaggy, scrolling in a browser or any other app looks typically as if there was no proper display driver installed. Heavily JavaScript-based sites are quite slow too. Videos play smoothly on the other hand... The funny thing is, that on the internal display of the netbook, everything is perfect. Now imagine this: I've an Epiphany window opened, pull it over to the internal display and it's perfect, take it back to the external, and becomes immediately jagged.

Any ideas? Thanks!

---

### Post by kosen on 2010-01-13
This is what I've just found on a blog :(

> 
Notes:
Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048×2048. The virtual screen can be larger but DRI will be disabled.


I still don't understand however, why the internal display works flawlessly...

---

### Post by kosen on 2010-01-13
Well, I've found a quasy-solution... :)

I've "arranged" the external display under the other - at least virtually. This way I could place both displays into a 2048x2048 virtual area. Like this:

[IMG]http://www.thinkwiki.org/images/a/ac/Intel-DualHead.png[/IMG]

It's a bit awkward yet, but hopefully I will get used to it soon.

---

