---
title: "GIGABYTE GA-990FXA-UD3 motherboard USB3 not working with 64 bit kernel"
date: 2016-07-21
forum: Hardware
---

### Post by bkorb on 2016-07-21
I've been here:
[GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel]("https://ubuntuforums.org/showthread.php?t=2111223")
which is a 970A thread with two 990FXA entries claiming success.
I've not had the same experience.  In that thread, adding ```
GRUB_CMDLINE_LINUX="iommu=soft"
``` and disabling iommu fixes the issue.  But not for me.  I've tried all combinations of IOMMU enabled and disabled with and without the CMDLINE change.  My keyboard, mouse, thumb drive and USB3.0 camera tether are all plugged into a USB3 hub.  They must be, as they are USB3 devices.  My thumb drive is seen, but nothing else.  (OK, haven't actually tried my camera tether, but without a keyboard, it's pretty pointless.)  I get this:
```
[  548.085054] usb 1-1: new high-speed USB device number 10 using xhci_hcd
[  548.218498] usb 1-1: New USB device found, idVendor=05e3, idProduct=0610
[  548.218506] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  548.218511] usb 1-1: Product: USB2.0 Hub
[  548.218514] usb 1-1: Manufacturer: GenesysLogic
[  548.219335] hub 1-1:1.0: USB hub found
[  548.220042] hub 1-1:1.0: 4 ports detected
[  548.524988] usb 2-1: new SuperSpeed USB device number 4 using xhci_hcd
[  548.547789] usb 2-1: New USB device found, idVendor=05e3, idProduct=0617
[  548.547796] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  548.547801] usb 2-1: Product: USB3.0 Hub
[  548.547805] usb 2-1: Manufacturer: GenesysLogic
[  548.549929] hub 2-1:1.0: USB hub found
[  548.550537] hub 2-1:1.0: 4 ports detected
[  548.616645] usb 1-1.1: new full-speed USB device number 11 using xhci_hcd
[  548.656292] hub 2-1:1.0: hub_port_status failed (err = -71)
[  548.714536] usb 1-1.1: New USB device found, idVendor=046d, idProduct=c245
[  548.714543] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  548.714549] usb 1-1.1: Product: Gaming Mouse G400
[  548.714552] usb 1-1.1: Manufacturer: Logitech
[  548.714830] usb 1-1.1: Not enough bandwidth for new device state.
[  548.714840] usb 1-1.1: can't set config #1, error -28
```"Not enough bandwidth" for a mouse or keyboard.  The thumb drive is okay because it will use whatever bandwidth is available, but the keyboard and mouse demand a minimum.

---

### Post by DuckHook on 2016-07-21
Did you remember to:```
sudo update-grub
```

---

### Post by oldfred on 2016-07-21
Some more info in this thread:
[https://ubuntuforums.org/showthread.php?t=2254677](https://ubuntuforums.org/showthread.php?t=2254677)

Keyboard & mouse do not need USB3 ports, they can easily run from USB2 ports.

---

### Post by gordintoronto on 2016-07-22
I routinely run USB3 devices on USB2 ports, no problem.

What version of Linux?

---

