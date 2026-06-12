---
title: "Use External Monitor  as Default"
date: 2010-02-13
forum: Hardware
---

### Post by sammyboy405 on 2010-02-13
Hello I wasn't sure if this would go in here or the Multimedia / Display Section.  

Heres is what I want to accomplish.  I have a HP DV7 (ATI 3500HD) Using the HDMI output to a HP w2338h Monitor.  Id like to use it exclusively as the DV7 LCD pretty much sucks. Fn-f4 does nothing for monitor switching unless im using the VGA d-sub output. Karmic 9.10

So here is what ive done thus far and have pretty much accomplished what im wanting.

Forced GDM to use the external Monitor by
Switched TTY from Login Screen (F1)
exported DISPLAY=:0.0
ran sudo -u gnome-control-center
switched back to X  (F7)
Clicked on Display and Disabled the Laptop LCD.

Now GDM does exactly what I want it to do.  

I accomplished the Rest with xorg.conf here is mine

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "0-LCD"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LCD" "0-LCD"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option		"UseDisplayDevice" "DFP-1, CRT"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Heres the Problem now/whats left to do.

1. Virtual TTY's goto Blank Screen.  I can only assume it is trying to goto my laptop LCD (as it worked prior to disabling the Laptop LCD on GDM)

2. Not even sure this is possible, could be a BIOS / Laptop Limitation display the GRUB menu on my External Display

3. Display the Ubuntu Splash on the External Display

If I could get those 3 items working my setup would be 100% perfect.

Id really like to get #1 working for sure id be #1 priority. then #3. But im pretty sure #2 is my laptop's lack of being able to set the BIOS to use the external display.

Any help would be much appreciated.

---

### Post by sammyboy405 on 2010-02-13
I guess another way to say what im looking for is :

How do you set the Primary Display for TTY's 1-6 ?  They all default goto my laptop display and I want them on my External Display.

---

### Post by dE_logics on 2010-05-27
There appears to be no ways.

---

