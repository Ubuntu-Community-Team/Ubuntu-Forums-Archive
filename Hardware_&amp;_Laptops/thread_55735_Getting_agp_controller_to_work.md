---
title: "Getting agp controller to work"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by nom on 2005-08-10
Heya, having some trouble getting my agp running properly.

Im running a 6600gt on a recent sis chipset, and have the nvidia drivers installed and they seem to be working properly (yet very slowly).

heres the display section out of my x conf.

```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAgp"		"3"
EndSection

Section "Monitor"
	Identifier	"T910B"
	Option		"DPMS"
EndSection
```

and Im asuming this is my undetected agp controller.

```
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
```

and video card

```
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1
```

any help would be appreciated ><  ](*,) 

cheers in advance, nom.

---

### Post by MrCheese on 2005-08-10
[QUOTE=nom]Heya, having some trouble getting my agp running properly.

Im running a 6600gt on a recent sis chipset, and have the nvidia drivers installed and they seem to be working properly (yet very slowly).

heres the display section out of my x conf.

[CODE]Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAgp"		"3"
EndSection



any help would be appreciated ><  ](*,) 

cheers in advance, nom.[/QUOTE]

Try commenting out the option for NvAGP - the system should then use the kernel agpgart module instead. If x fails to fire up log on at the console & "modprobe agpgart" & see if the system actually loads the agp driver. You can then startx manually.

---

### Post by nom on 2005-08-10
commented it out still seems to be the same trouble, agpgart is running too.

Cheers

---

