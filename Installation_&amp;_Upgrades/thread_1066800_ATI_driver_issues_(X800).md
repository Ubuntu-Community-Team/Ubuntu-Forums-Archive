---
title: "ATI driver issues (X800)"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by PendragonUK on 2009-02-11
I have just build a PC for my wife from bits salvaged parts bin. As expected the install went fine until I tried to use the restricted drivers for the ATI card.

On reboot I get this message:-

Ubuntu is running in low-graphic mode

(EE) fglrx(0): DRIScreenlnid failed!
(EE) fglrx(0): FB pci_device_map_range error!
(EE) fglrx(0): failed to map FB memory
(EE) fglrx(0): ===[selDalHelperSetControllerConfigerRemap]===
CUDDC ControllerSetConfig failed: 6-0
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9

The G/Card is an ATI X800 256Mb AGP 
MoBo ASUS A8V Deluxe
CPU AMD Athlon 3500+ 64

---

### Post by PendragonUK on 2009-02-11
Resolved

Downloaded driver from the AMD/ATI site and did a manual install.

---

