---
title: "SiS M760GX (Acer Aspire) video flickers in Edgy"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by crazybilly on 2007-02-12
I'm running Edgy on my Acer Aspire 3003WLmi .  After installing ndiswrapper and blacklisting bcm43xx, it's running pretty well.

I've got some video issues, I think, though--the screen occasionally flickers, or rather, has a flickery band run across it.  I've seen the screen do this before, on Windows, when the generic driver was installed.  It went away once I installed Acer's driver.  So, clearly, I've not got the perfect driver installed.

I can follow directions well (and haven't had much luck googling this problem), but I'm still learning how to troubleshoot problems like this.  Any help would be appreciated.  Thanks!

---

### Post by crazybilly on 2007-02-12
Update:  

I edited /etc/xorg.conf to change the video driver.  It was set to "vesa" and I changed it to "sis".

Here's the section I changed:

```
Section "Device"
	Identifier	"Generic Video Card"
#changed the following from  from "vesa"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection
```

That seems to have solved the problem (I'm not noticing any flickers).  If I have problems, I'll post back, but I think I got that one solved.

---

### Post by dennis1200 on 2007-02-21
I have this card too, and it's not a great one, especially in Ubuntu (no DRI/3d support). In terms of flicker, however, there is a hardware reason for that, independent of operating system. See [http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13) for a rundown on the problems with the 760 chipset.

---

