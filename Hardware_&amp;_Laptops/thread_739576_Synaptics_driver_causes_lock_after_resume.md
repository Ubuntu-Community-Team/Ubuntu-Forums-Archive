---
title: "Synaptics driver causes lock after resume"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by mikej_96 on 2008-03-29
Hello, I have a gateway laptop that uses the synaptics driver. This driver appears to be causing a hard lock whenever the touchpad is used after a resume from a suspend to ram. 
I think it is the synaptics driver, or the way it is configured in xorg.conf because, the system suspends and resumes just fine, and doesn't lock if the touchpad isn't used. A usb mouse can be used without problem, but after a while of using the touchpad, the system locks and a hard restart is required. 

Here is a clipping from my xorg.conf
Section "InputDevice"
	Identifier 	        "Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents" "true"
        Option              "Device"                 "/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"true"
       Option               "HorizEdgeScroll"    "0"
EndSection


Any ideas of how to fix this? A workaround would be sweet. 
Thanks.

---

