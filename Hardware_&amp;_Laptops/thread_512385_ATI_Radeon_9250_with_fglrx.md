---
title: "ATI Radeon 9250 with fglrx"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by slaenner on 2007-07-29
Hi,

I have a ATI Radeon 9250 which I'm trying to get running on my Ubuntu 7.04. As the driver from ATI does not run under Xorg 7.2 I'm trying to use the fglrx driver (which I belive should run under Xorg 7.2?). So I install fglrx using synaptic and edit my /etc/X11/xorg.conf file to use the fglrx driver in the Device section for my graphics card:
```

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART" "no"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

```

When I try to load X i receive this is what I get:
```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

I have attached my complete xorg.conf file and the complete X server output log.

Hope somebody can help.

---

### Post by eggdeng on 2007-07-29
ATI cards under 9500 are not supported under fglrx according to [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

