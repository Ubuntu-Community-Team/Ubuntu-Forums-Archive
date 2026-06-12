---
title: "Horrible GPU performance"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by domesticatewhat on 2005-08-05
I have read at least 10 threads about the IGP 320m from ATI but I am getting ~105 fps in glxgears.

Although there is no 3D support for this card it seems it should be a little higher than that.

Any suggestions?

athlon xp-m 2400
ati igp 320m
hoary
i686 kernel

---

### Post by s_p_a_r_k_y on 2005-08-05
are you using vesa video drivers? Or ati? or radeon? Do you have GLX enabled in xorg.conf?

---

### Post by domesticatewhat on 2005-08-05
I have glx enabled and here is my device section in xorg.conf

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
```

Here is the loaded modules

> 
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection


---

### Post by varunus on 2005-08-05
You need to install the proprietary ATI drivers if you want good performance.  Try this howto:
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

Read the whole thing first.  You should zip along with 3d if your card is supported by the ATI drivers.  If it isn't, you can try the newest version of the ATI drivers (harder to install) with this howto:
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)

---

### Post by domesticatewhat on 2005-08-05
ATI 320m isn't supported by the fglrx driver.

---

