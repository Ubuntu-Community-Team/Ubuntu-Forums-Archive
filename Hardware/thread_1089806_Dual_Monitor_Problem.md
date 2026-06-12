---
title: "Dual Monitor Problem"
date: 2009-03-07
forum: Hardware
---

### Post by ccumbie2889 on 2009-03-07
Hello, I'm having an issue with setting up my dual monitors in Ubuntu Intrepid. I have an ATI All-in-Wonder HD, which is a Radeon 3650 w/ a TV tuner. Both of my monitors are 1440x900 native resolution. One is an Hannspree HF199H connected via HDMI, and the other is an Acer P191w connected via DVI. I can use the generic driver to get the big desktop with 2880x900 resolution, but the login screen is mirrored, and each screen is a different resolution. When I install the fglrx driver, and use Catalyst Control Center, I select big desktop, and it makes the resolution 5760x900, and it cannot be changed. When I logout, the login screen is this resolution, once I log in, the desktop goes back to a mirrored display with 1440x900 resolution. Any ideas? Here is my xorg.conf...




Section "Monitor"
      Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2880 900
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

---

