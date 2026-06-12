---
title: "External HD not showing. Why?"
date: 2014-10-11
forum: Hardware
---

### Post by Robbyx on 2014-10-11
I have just reinstalled Ubuntu Gnome 14.04. My external HD is not being recognised by blockid.

What does the following mean ( I had pulled out the USB 3 cable and power to the HD and put it back in again )

```
robins@robins-EP35-DS3L:~$ dmesg | tail -n 35
[32128.340075] hub 10-0:1.0: unable to enumerate USB device on port 2
[32128.704262] usb 10-2: new SuperSpeed USB device number 6 using xhci_hcd
[32133.720418] usb 10-2: device descriptor read/8, error -110
[32133.824009] usb 10-2: new SuperSpeed USB device number 6 using xhci_hcd
[32138.840392] usb 10-2: device descriptor read/8, error -110
[32139.316262] usb 10-2: new SuperSpeed USB device number 7 using xhci_hcd
[32144.332421] usb 10-2: device descriptor read/8, error -110
[32144.436013] usb 10-2: new SuperSpeed USB device number 7 using xhci_hcd
[32149.452395] usb 10-2: device descriptor read/8, error -110
[32149.928267] usb 10-2: new SuperSpeed USB device number 8 using xhci_hcd
[32154.944420] usb 10-2: device descriptor read/8, error -110
[32155.048014] usb 10-2: new SuperSpeed USB device number 8 using xhci_hcd
[32160.064392] usb 10-2: device descriptor read/8, error -110
[32160.540264] usb 10-2: new SuperSpeed USB device number 9 using xhci_hcd
[32165.556416] usb 10-2: device descriptor read/8, error -110
[32165.660011] usb 10-2: new SuperSpeed USB device number 9 using xhci_hcd
[32170.676406] usb 10-2: device descriptor read/8, error -110
[32170.780086] hub 10-0:1.0: unable to enumerate USB device on port 2
[32171.144258] usb 10-2: new SuperSpeed USB device number 10 using xhci_hcd
[32176.160418] usb 10-2: device descriptor read/8, error -110
[32176.264011] usb 10-2: new SuperSpeed USB device number 10 using xhci_hcd
[32181.280394] usb 10-2: device descriptor read/8, error -110
[32181.756264] usb 10-2: new SuperSpeed USB device number 11 using xhci_hcd
[32186.772419] usb 10-2: device descriptor read/8, error -110
[32186.876017] usb 10-2: new SuperSpeed USB device number 11 using xhci_hcd
[32191.892395] usb 10-2: device descriptor read/8, error -110
[32192.368264] usb 10-2: new SuperSpeed USB device number 12 using xhci_hcd
[32197.384420] usb 10-2: device descriptor read/8, error -110
[32197.488010] usb 10-2: new SuperSpeed USB device number 12 using xhci_hcd
[32202.504390] usb 10-2: device descriptor read/8, error -110
[32202.980264] usb 10-2: new SuperSpeed USB device number 13 using xhci_hcd
[32207.996419] usb 10-2: device descriptor read/8, error -110
[32208.100014] usb 10-2: new SuperSpeed USB device number 13 using xhci_hcd
[32213.116396] usb 10-2: device descriptor read/8, error -110
[32213.220033] hub 10-0:1.0: unable to enumerate USB device on port 2

```

I have done some searches on the error but could not find anything of use. 
gparted run from within ubuntu does not show the external HD. 

Maybe I have fogotten how to install the USB 3 device. Isn't it  automatic, but I have just reinstalled the os so perhaps I have left something out. Any ideas?

---

### Post by TheFu on 2014-10-11
On some systems USB3 is broken as long as USB2 is enabled. There is a setting in BIOS to disable XHCI on the USB2 ports.  This is what I had to do here, which sucks since there are 8 USB2 ports on the machine, but only 4 USB3 ports on the add-in card.  Still, having the USB3 performance (which didn't work any other way) is worth it. The older ports are only USB 1.1 now - fine for mice and keyboards, not storage or video devices.

Did the same thing on another box - worked.  It didn't have the XHCI setting at all, just had to disable all USB2 ports completely.

Shot in the dark really.

---

### Post by Robbyx on 2014-10-11
I have just reinstalled UbuntuGnome 14.04. Yesterday I had the external HD working in UG 14.04. Now following the fresh install, it is not recognising the Ext HD! I suspect that it has nothing to do with USB2 because there has been no change in the computer's hardware. Can you suggest any other solutions that I could try?

---

### Post by Robbyx on 2014-10-11
I have just run fsck -fyC /dev/sda2 and sda3 ie home and root via the command line in the recovery mode.. The external hd has come back! I am going to check if the error messages are still there. I did see them before I ran fsck. I hope they have gone away.

---

