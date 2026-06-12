---
title: "Resolution on my server (no mointor, VNC only)"
date: 2009-01-30
forum: Hardware
---

### Post by MisterM on 2009-01-30
Hi,

I followed some of the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=51587]("http://ubuntuforums.org/showthread.php?t=51587"). After fiddling with the xorg.conf file, I managed to get the resolution on my server up to 1280x1024. However, I have a wide screen on my client and would like to have a wide resolution on the server too. It seems though, that whatever I put in the xorg.conf file, I always get the same resolutions to pick from.

This is my current xorg.conf file:
```
Section "Device"
	Identifier	"NV6600GT"
	Driver		"vesa"
	Option	        "NoDCC"	"true"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync       30.0 - 81.0
	VertRefresh     54.0 - 75.0
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Device          "NV6600GT"
	Monitor         "Generic Monitor"
	DefaultDepth    24
	SubSection "Display"
		Depth           24
		Modes           "1920x1080" "1440x900"
	EndSubSection
EndSection
```

These are the resolutions I can pick from:
320x200, 640x400, 640x480, 800x600, 1024x768, 1280x1024

How can I get it to offer me the resolutions that I have specified in the xorg.conf file?

---

### Post by MisterM on 2009-01-31
Anyone? :(

---

