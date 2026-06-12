---
title: "VT8378 [S3 UniChrome]  on KM400/A Chipset"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by TenPlus1 on 2008-01-25
I have a great Asus motherboard running the KM400/A chipset and a VT8378 [S3 UniChrome] Integrated Video card that runs really well on WinXP *cough*, but I really wish the 3D would work on Ubuntu also as I am missing out on some really cool games and screensavers...

I'm pretty happy with how it works so far, direct rendering using the xserver-xorg-video-unichrome driver (not via) and my xorg.conf looking like this:

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
#	Option 		"VBEModes" "true" <-- this crashes anything 3D
	Option 		"DisableIRQ"
	Option 		"EnableAGPDMA"
	BusID		"PCI:1:0:0"
EndSection

but I would like to know if anyone has actually gotten the 3D to work properly ???

---

### Post by overdrank on 2008-01-25
> **TenPlus1 said:**
> I have a great Asus motherboard running the KM400/A chipset and a VT8378 [S3 UniChrome] Integrated Video card that runs really well on WinXP *cough*, but I really wish the 3D would work on Ubuntu also as I am missing out on some really cool games and screensavers...

I'm pretty happy with how it works so far, direct rendering using the xserver-xorg-video-unichrome driver (not via) and my xorg.conf looking like this:

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
#	Option 		"VBEModes" "true" <-- this crashes anything 3D
	Option 		"DisableIRQ"
	Option 		"EnableAGPDMA"
	BusID		"PCI:1:0:0"
EndSection

but I would like to know if anyone has actually gotten the 3D to work properly ???

HI and maybe this can be of some help
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by TenPlus1 on 2008-01-26
Thanks for the link, I gave it a go, found the appropriate driver for my card and installed everything without any problems... but... it will not allow my screen res of 1280x1024 and my mouse pointer has disappeared...  I fiddled for a while and could not get my mouse to return, so eventually uninstalled the driver and it all works again, apart from my Direct Rendering which has somehow gone... oh well...  I'll wait and see what Hardy comes up with in the hope of a working driver...

---

### Post by overdrank on 2008-01-26
> **TenPlus1 said:**
> Thanks for the link, I gave it a go, found the appropriate driver for my card and installed everything without any problems... but... it will not allow my screen res of 1280x1024 and my mouse pointer has disappeared...  I fiddled for a while and could not get my mouse to return, so eventually uninstalled the driver and it all works again, apart from my Direct Rendering which has somehow gone... oh well...  I'll wait and see what Hardy comes up with in the hope of a working driver...

HI and I have heard that some user change the default depth from 24 to 16 and this helps with the resolution. As for the direct rendering I can not help. :(

---

### Post by TenPlus1 on 2008-01-26
I gave the 16 bit depth a go and still the same problem, go figure...  I'll stick with the unichrome driver for now and maybe something will crop up soon to help everyone with UniChrome cards wanting 3D...

---

