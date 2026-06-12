---
title: "USB External Hard Drive Crash?"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by Tsen on 2007-04-09
I've got a 250 GB external "SimpleTech" hard drive, but it seems to be acting up lately.  I'm worried that it might be because of physical damage to the drive (I dropped it about a foot onto a chair the other day), but it read fine when I plugged it into my home computer after that.  When I brought it back up to school, though, it started giving me issues.
When I plug in the drive in Windows, the system makes the new device plugged in sound, but doesn't recognize the drive or show a drive letter under "My Computer".  Afterwards, the system begins to hang and the "System Idle Process" locks up the processor, I'm guessing because it keeps trying to access the drive and doesn't have a maximum number of tries before it gives up.
When I plug it in under Ubuntu, it recognizes the device, shows an icon for it on the desktop, and automatically opens a window to show the contents of the drive, but the window is blank.  The system tries to read the drive for a bit longer, then it gives me a "Unsafe Device Removal" warning and the icon disappears from the desktop.
When I run dmesg, I get this message repeatedly:
[  397.404432] scsi 5:0:0:0: rejecting I/O to dead device

Followed by this:
[  397.595228] usb 4-4: device descriptor read/64, error -71
[  397.811199] usb 4-4: new high speed USB device using ehci_hcd and address 12
[  397.923175] usb 4-4: device descriptor read/64, error -71
[  398.139081] usb 4-4: device descriptor read/64, error -71
[  398.355030] usb 4-4: new high speed USB device using ehci_hcd and address 13
[  398.762912] usb 4-4: device not accepting address 13, error -71
[  398.874903] usb 4-4: new high speed USB device using ehci_hcd and address 14
[  399.282781] usb 4-4: device not accepting address 14, error -71

So, basically, what exactly does this mean?  And is there any way to try and recover the data on the drive (I had 45 GB of music, 20 GB of Linux distros and a bunch of photos on there that I'm not sure I can replace)?

---

### Post by teaker1s on 2007-04-10
assuming that the drive is damaged, you may want to contact the manufacturer-most manufacturers have disk health check and repair utilities.
Sometimes they can remove bad sectors from disk table and the disk is in effect repaired

---

