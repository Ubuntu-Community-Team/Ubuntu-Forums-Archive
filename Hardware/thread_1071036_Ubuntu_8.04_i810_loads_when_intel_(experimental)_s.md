---
title: "Ubuntu 8.04 i810 loads when intel (experimental) specified"
date: 2009-02-15
forum: Hardware
---

### Post by pbrannen on 2009-02-15
Folks,

I'm trying to build an ubuntu boxee box, and I have an older intel integrated video card:

00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)

Boxee will not work with the i810 driver, so they say to use the intel driver.  I've specified in my xorg.conf:

Section "Device"
  Identifier  "Card0"
  Driver      "intel"
  VideoRam    32000
  Option      "NoAccell"      "0"
  Option      "DCC"           "1"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth	16
	Device		"Card0"
	SubSection "Display"
  		Depth 16
  		Modes "1440x900"
 	EndSubSection
EndSection

However, an lsmod shows that the i810 is still being loaded:

Module                  Size  Used by
i810                   19968  2 

Am I missing something?  Is there anyway to determine which driver is being loaded and whether or not it's the intel experimental driver?

Thanks,
Patrick

---

### Post by nixscripter on 2009-02-17
That driver might not be the problem. The naming of kernel vs. X drivers is not consistent.

If you think the driver is the problem, you can add it to **/etc/modprobe.d/blacklist** with the line: ```
blacklist i810
```

If you reboot and it doesn't work, you can take the line back out again.

---

### Post by Vico Vicario on 2009-02-18
Study the logs /var/log/Xorg.0.log . Look for LoadModule.

There might be an error in the config file.

Also, Xorg module name is intel, but kernel module might have another name. In my case is i915 and intel_agp.

V.

---

