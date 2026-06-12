---
title: "Extrnal USB HDD not mounting"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by jcoolkatzerg on 2007-09-13
I have had Ubuntu 7.07 installed for about 6 months now, and about 2 weeks ago, my external HDD stopped mounting automatically, even after rebooting.  Since this happened, I have not been able to mount/use any other USB device except for the USB mouse that I use with the system.  I have spent the last two weeks trying to figure this out on my own, but I have made no progress.  Yes, I have searched this and a few other sites, but I have yet to find a solution that works.

Relevant info:

140 GB 3.5" IDE HDD in a USB 2.0 enclosure using 
2 NTFS partitions, 60 GB and 80 GB
Still mounts normaly on my Win XP laptop
Indicator light is off, but fan is running and the drive is spinning (On == normal operation/powered, flashing == read/write, off == error?)
Does not show up in blkid
Does show up in Device Manager
Not a power issue (uses 120v wall power)
Not a cable issue (I've tried 3 different ones, and they all work on other machines)

Print out from dmesg:
```
[26558.562033] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26588.991330] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26619.420616] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26649.845931] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26680.275221] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26710.700536] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26711.046659] sd 3:0:0:0: SCSI error: return code = 0x00050000
[26711.046677] end_request: I/O error, dev sdc, sector 124921279
[26711.046685] Buffer I/O error on device sdc1, logical block 124921216
[26711.046693] Buffer I/O error on device sdc1, logical block 124921217
[26711.046698] Buffer I/O error on device sdc1, logical block 124921218
[26711.046703] Buffer I/O error on device sdc1, logical block 124921219
[26711.046708] Buffer I/O error on device sdc1, logical block 124921220
[26711.046713] Buffer I/O error on device sdc1, logical block 124921221
[26711.046717] Buffer I/O error on device sdc1, logical block 124921222
[26711.046722] Buffer I/O error on device sdc1, logical block 124921223
[26741.153799] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26771.579091] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26802.004390] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26832.217913] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26862.643216] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26893.068503] usb 5-3: reset high speed USB device using ehci_hcd and address 20
[26893.408083] sd 3:0:0:0: SCSI error: return code = 0x00050000
[26893.408090] end_request: I/O error, dev sdc, sector 312576480
[26893.408098] Buffer I/O error on device sdc2, logical block 187655040
[26893.408106] Buffer I/O error on device sdc2, logical block 187655041
[26893.408111] Buffer I/O error on device sdc2, logical block 187655042
[26893.408116] Buffer I/O error on device sdc2, logical block 187655043
[26893.408144] Buffer I/O error on device sdc2, logical block 187655044
[26893.408149] Buffer I/O error on device sdc2, logical block 187655045
[26893.408154] Buffer I/O error on device sdc2, logical block 187655046
[26893.408159] Buffer I/O error on device sdc2, logical block 187655047
```

If there is any other information that you need, let me know, and I'll grab it ASAP.

---

### Post by bobonthenet on 2007-09-18
I think I'm having the same problem.  I only just noticed it today though and I use the drive frequently.

---

