---
title: "VMWare Workstation + ATI Mobility HD 4570 + Proprietary Drivers = Problem"
date: 2011-01-21
forum: Hardware
---

### Post by nishant.singh28 on 2011-01-21
I'm trying to run a 32 bit Windows 7 guest on VMWare Workstation 7.13. But for some reason, I'm unable to get the 3d Graphics acceleration to work.
I'm running a 64 bit Meerkat system as the host. It has ATI Mobility Radeon HD 4570. I had uninstalled the ATI catalyst drivers some time beck to try out the open-source drivers. Since then, the Additional Hardware program stopped detecting my card. When I tried to reinstall the Catalyst drivers (the open-source ones caused severe heating and the battery life took a hit). I could not install it using Additinl Hardware because it did not detct the card. Installing fglrx and amdcccle from the Package Manager didn't help either. I had to install the .run package from ATI support site.
Now, VMWare says hardware driver is not configured properly. I tried using DRIconf, but that did not detect the driver either
```
$ driconf
Driver "fglrx" is not installed or does not support configuration.
```
and it starts in expert mode.
```
$ sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: M92 [Mobility Radeon HD 4500 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:d0000000-dfffffff ioport:2000(size=256) memory:fc000000-fc00ffff memory:fc020000-fc03ffff
$ sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: M92 [Mobility Radeon HD 4500 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:d0000000-dfffffff ioport:2000(size=256) memory:fc000000-fc00ffff memory:fc020000-fc03ffff

```
and
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 1.4 (3.3.10317 Compatibility Profile Context)

```
and my xorg.conf
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

[This]("http://communities.vmware.com/thread/273969?tstart=0") is the thread that describes what I need to do
What am I supposed to do to get working??


EDIT: The damn thing works for the first time after a reboot

---

### Post by nishant.singh28 on 2011-01-24
Bump

---

### Post by nishant.singh28 on 2011-02-07
Bumpity bump!!!

---

### Post by nishant.singh28 on 2011-02-26
Bump again...come on someone!!!

---

### Post by nishant.singh28 on 2011-04-23
Bump again!!!

---

