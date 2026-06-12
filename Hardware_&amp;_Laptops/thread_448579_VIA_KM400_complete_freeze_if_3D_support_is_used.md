---
title: "VIA KM400: complete freeze if 3D support is used"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by narr on 2007-05-19
Hi,

I get a complete system freeze (mouse cursor excluded) every time I start any 3D application such as glxgears.

Even a simple 'glxinfo | grep direct direct rendering' freezes the system.

I don't know why and don't know where to search for error messages.

My xorg.conf looks like this:

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	Option "VBEModes" "true"
	Option "DisableIRQ"
	Option "EnableAGPDMA" 
	BusID		"PCI:1:0:0"
EndSection

Everything worked fine under Dapper and Edgy.

Any ideas?

---

