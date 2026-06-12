---
title: "Scanner canon 650U not working"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by rflint on 2005-05-08
I don't anderstand why my scanner USB Canon 650U doesn't work.

It is recognise by sane :

>sane-find-scanner
>
> # No SCSI scanners found. If you expected something different, make sure that
>  # you have loaded a SCSI driver for your SCSI adapter.
>  # Also you need support for SCSI Generic (sg) in your operating system.
>  # If using Linux, try "modprobe sg".
>
> found USB scanner (vendor=0x04a9 [Canon], product=0x2206 [CanoScan], 
>  chip=LM9832/3) at libusb:002:010

xsane start but when i start to scan i have a error :
> dmesg
>
> usb 2-1: new full speed USB device using uhci_hcd and address 9
> usb 2-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 5 ret -71
> usb 2-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 4 ret -71


Anyone have i idea (or some other test to do)

Thank for help

---

### Post by russelld on 2005-09-21
I'm getting the same problem.
The scanner is seen at the usb port, but when it comes to scanning it fails, though works in Win98
I have tried a Canon N1240U which uses the same chipset and it works in Ubuntu.

xsane finds the scanner, but when it goes to scan or preview a dialog box pops up with:
Failed to start scanner.  Error during I/O.

lsusb:
Bus 001 Device 007: ID 04a9:2206 Canon, Inc. CanoScan N650U/N656U
Bus 001 Device 001: ID 0000:0000 

sane-find-scanner -v :
This is sane-find-scanner from sane-backends 1.0.15

searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
....
searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
......
checking /dev/usbscanner15... failed to open (Invalid argument)
found USB scanner (vendor=0x04a9 [Canon], product=0x2206 [CanoScan], chip=LM9832
/3) at libusb:001:026
# Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

scanimage -L:
device `plustek:libusb:001:007' is a Canon N650U/N656U USB flatbed scanner

dmesg reports:
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 5 ret -110
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 4 ret -110
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 4 ret -110
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 5 ret -110
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 4 ret -110
Sep 21 22:35:40 localhost last message repeated 2 times
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 5 ret -110
Sep 21 22:35:40 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x3 len 4 ret -110
Sep 21 22:35:40 localhost kernel: usb 1-1: USB disconnect, address 10
Sep 21 22:35:40 localhost kernel: usb 1-1: new full speed USB device using ohci_hcd and address 11
Sep 21 22:35:42 localhost usb.agent[20704]:      libusbscanner: loaded successfully

any clues?

---

### Post by russelld on 2005-10-23
It works!
I did a scan today and printed copy off for a friend

This box was upgrading to Breezy on Thursday .

Now I don't have to network a windows box to do this.

Thanks devs for fixing it!

---

### Post by oliwally on 2005-11-08
I have the same scanner running on Kubuntu 5.10. It works, but the scan is overexposed on one side. So, half the page is good, but the other half is overexposed and unusable (Eg. when scanning A4 colour page, left side is overexposed, right side is good). The scanner works fine in WinXP.

Does anyone have any ideas how to fix this?

---

### Post by infinitezero on 2007-05-14
I am having the same issue with feisty, one side overexposed. Does anyone know how to fix the issue?


Thanks,
iz

---

