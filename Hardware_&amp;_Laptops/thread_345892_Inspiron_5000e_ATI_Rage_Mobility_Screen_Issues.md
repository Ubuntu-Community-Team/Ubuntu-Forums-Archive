---
title: "Inspiron 5000e ATI Rage Mobility Screen Issues"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by brownman98 on 2007-01-24
I am using an old Dell Inspiron 5000e for a project and am using Ubuntu 6.10. I was having some issues with getting the screen to display correctly with the ATI Rage Mobility card. I came across these two links that fixed everything. This may not help that many people out there but I thought I would post it.

[http://users.linpro.no/janl/hardware/inspiron-5000.html](http://users.linpro.no/janl/hardware/inspiron-5000.html)
[http://ibgwww.colorado.edu/~lessem/5000e/](http://ibgwww.colorado.edu/~lessem/5000e/)

Sample xorg.conf settings for the driver
----------------------------------------------------------

Section "Device"
	### Available Driver options are:-
        #Option     "NoAccel"
        #Option     "SWcursor"
        #Option     "HWcursor"
        #Option     "Dac6Bit"
        #Option     "Dac8Bit"
        #Option     "ForcePCIMode"
        #Option     "CCEPIOMode"
        #Option     "CCENoSecurity"
        #Option     "CCEusecTimeout"
        Option     "AGPMode" "2"
        #Option     "AGPSize"
        #Option     "RingSize"
        #Option     "VBListSize"
        #Option     "VBSize"
        #Option     "UseCCEfor2D"
        #Option     "EnableFP"
        #Option     "CRTOnly"
        #Option     "UseFBDev"
#	Option      "ProgramFPRegs" "false"
        Option       "DPMS"
	Option      "Display" "Mirror"
	Identifier  "Card0"
#	Driver      "r128"
	Driver      "ati"
	VendorName  "ATI"
	BoardName   "Rage 128 Mobility LF"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by kevdog on 2007-03-18
Total newbie to ubuntu -- having display problems during installation of edgy from live cd.  I understand I need to change something in the xorg.conf file.  Can you be more specific --- Specifically how do I install Ubuntu initially -- text only??? and when do I change the xorg.conf file???

---

### Post by zantzinger on 2007-03-18
This is exactly my problem - 5000e with ATI Rage Mobility 128, not displaying properly. Will try to work through those two links but as a total newbie I may come crying for help

---

