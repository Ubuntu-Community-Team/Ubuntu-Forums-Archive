---
title: "glxgears freezes on mouse movements"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by domesticatewhat on 2005-08-12
I am still having trouble with my laptop.

It has an **ati 320m** chipset. 

Everything works correctly but 3D accel. (which I know will probably never work). When I run glxgears I get ~150 fps and if I move my mouse the computer will freeze.

I know your probably saying "then don't run glxgears" but I would like to know what is causing this?

I have athlon Xp 1800 693mb RAM. I am using the 2.6.10-5-k7 kernel and here is my device config.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection
```

---

### Post by Lord Illidan on 2005-08-12
Try and search around how to enable ATI gl support.. People have done it under Linux, although I have an NVIDIA card which gives me no problems..

---

### Post by domesticatewhat on 2005-08-12
are you referring to official ati drivers? (fglrx..or something like that) if so those will not work with my card.

---

### Post by Copter on 2005-08-14
i have the same problem on 9100 IGP. when i use standard (Driver "ati") drivers i get 150 fps on glxgears. when using fglrx, system just hangs / freezes / crashes without any error messages.

anyone know what can be wrong here?

copter :]

---

