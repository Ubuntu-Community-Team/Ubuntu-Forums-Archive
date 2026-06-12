---
title: "Logitech V200 mouse not detected"
date: 2008-07-23
forum: Hardware
---

### Post by sullydog101 on 2008-07-23
I have been trying to troubleshoot this for a few hours now and am a loss. 
I have a Logitech wireless usb mouse V200 that does not work in my clean installation of Hardy Heron. I was previously using Gutsy Gibbon and it worked fine. I am fairly new with Linux, so I don't know all that much about making it work. The mouse works on my Vista partition, so the mouse is not malfunctioning. My synaptics touchpad works fine as does another logitech mouse that I tried(this one is corded, not sure of the model). I would appreciate any assistance on the matter. 

in my xorg.conf file this is the mouse script that is in there:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

when I type in cat/proc/input/devices 

the mouse section i get is:

I: Bus=0003 Vendor=046d Product=c510 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input13
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20017
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10
B: LED=ff00

so it seems as if linux sees it but it doesn't work at all! any help would be greatly appreciated!

Thanks,

---

