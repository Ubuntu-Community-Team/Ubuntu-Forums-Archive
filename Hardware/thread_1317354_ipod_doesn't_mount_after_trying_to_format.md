---
title: "ipod doesn't mount after trying to format"
date: 2009-11-06
forum: Hardware
---

### Post by carlocossette on 2009-11-06
I attempted at formating an iPod 3G (10gig) that had previously been used on a Mac, so that I could install Rockbox. It showed the drive and the possibility to format it. However, at the end of the formating process, it gave me the following error:

"Error creating file system: helper exited with exit code 1: helper failed with:
Total number of sectors (19465648 ) not a multiple of sectors per track (32)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test"

I safely unmounted the device and tried reconnecting it, but it could no longer be recognized on my desktop. I tried a hard reboot on the iPod (while connected and disconnected). Here are the last few lines of dmesg in terminal:

[149085.312041] usb 7-1: new full speed USB device using uhci_hcd and address 19
[149085.720030] usb 7-1: device not accepting address 19, error -71
[149085.832050] usb 7-1: new full speed USB device using uhci_hcd and address 20
[149086.240054] usb 7-1: device not accepting address 20, error -71
[149086.240077] hub 7-0:1.0: unable to enumerate USB device on port 1
[149292.168056] usb 7-1: new full speed USB device using uhci_hcd and address 21
[149292.288055] usb 7-1: device descriptor read/64, error -71
[149292.512054] usb 7-1: device descriptor read/64, error -71
[149292.728069] usb 7-1: new full speed USB device using uhci_hcd and address 22
[149292.852041] usb 7-1: device descriptor read/64, error -71
[149293.076042] usb 7-1: device descriptor read/64, error -71
[149293.292055] usb 7-1: new full speed USB device using uhci_hcd and address 23
[149293.704034] usb 7-1: device not accepting address 23, error -71
[149293.816042] usb 7-1: new full speed USB device using uhci_hcd and address 24
[149294.232356] usb 7-1: device not accepting address 24, error -71
[149294.232379] hub 7-0:1.0: unable to enumerate USB device on port 1

I read similar problems that were solved with rmod ehci-hcd, but I get 
"ERROR: Module ehci_hcd does not exist in /proc/modules"

Any thoughts? Any info will be greatly appreciated.

---

