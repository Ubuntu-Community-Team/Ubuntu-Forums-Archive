---
title: "edgy hangs up when starting my webcam"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by maalvin15 on 2006-11-12
my edgy eft hangs up when starting the camorama.. anyone pls help me..

uname -r
2.6.17-10-386
 
lsmod | grep spca5xx
spca5xx               681552  0 
videodev                9728  2 pwc,spca5xx
usbcore               130304  5 pwc,spca5xx,ehci_hcd,uhci_hcd
 
dmesg | tail -n 5
[17180408.496000] pwc Philips webcam module version 9.0.2-unofficial loaded.
[17180408.496000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[17180408.496000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[17180408.496000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[17180408.500000] usbcore: registered new driver Philips webcam

I ATTACHED HERE THE RESULT OF MODINFO SPCA5XX

---

### Post by sabitha on 2006-11-12
my edgy hangs up to when the first time i use that with gyachI but after restart my computer the webcam fine.

---

