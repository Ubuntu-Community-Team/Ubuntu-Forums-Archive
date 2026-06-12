---
title: "Ipod Not Recognized, im desperate"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by escobar5 on 2006-06-06
Hello, i'm having problems with my ipod, it is a 3rd Gen Ipod, Windows Formated, and here's the dmesg output:

```

[4294776.320000] usb 4-2: new full speed USB device using uhci_hcd and address 2[4294776.433000] usb 4-2: device descriptor read/64, error -71
[4294776.647000] usb 4-2: device descriptor read/64, error -71
[4294776.850000] usb 4-2: new full speed USB device using uhci_hcd and address 3[4294776.963000] usb 4-2: device descriptor read/64, error -71
[4294777.177000] usb 4-2: device descriptor read/64, error -71
[4294777.380000] usb 4-2: new full speed USB device using uhci_hcd and address 4[4294777.788000] usb 4-2: device not accepting address 4, error -71
[4294777.890000] usb 4-2: new full speed USB device using uhci_hcd and address 5[4294778.298000] usb 4-2: device not accepting address 5, error -71
[4294780.415000] usb 5-8: new high speed USB device using ehci_hcd and address 6[4294780.529000] usb 5-8: device descriptor read/all, error -71
[4294780.632000] usb 5-8: new high speed USB device using ehci_hcd and address 7[4294780.746000] usb 5-8: device descriptor read/all, error -71
[4294788.320000] usb 4-2: new full speed USB device using uhci_hcd and address 6[4294788.433000] usb 4-2: device descriptor read/64, error -71
[4294788.647000] usb 4-2: device descriptor read/64, error -71
[4294788.850000] usb 4-2: new full speed USB device using uhci_hcd and address 7[4294788.963000] usb 4-2: device descriptor read/64, error -71
[4294789.177000] usb 4-2: device descriptor read/64, error -71
[4294789.380000] usb 4-2: new full speed USB device using uhci_hcd and address 8[4294789.788000] usb 4-2: device not accepting address 8, error -71
[4294789.890000] usb 4-2: new full speed USB device using uhci_hcd and address 9[4294790.298000] usb 4-2: device not accepting address 9, error -71
[4294792.165000] usb 5-8: new high speed USB device using ehci_hcd and address 10
[4294792.370000] Initializing USB Mass Storage driver...
[4294792.370000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294792.371000] usb-storage: device found at 10
[4294792.371000] usb-storage: waiting for device to settle before scanning
[4294792.371000] usbcore: registered new driver usb-storage
[4294792.371000] USB Mass Storage support registered.
[4294797.476000] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[4294797.587000] usb 5-8: device descriptor read/64, error -71
[4294797.812000] usb 5-8: device descriptor read/64, error -71
[4294798.015000] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[4294798.131000] usb 5-8: device descriptor read/64, error -71
[4294798.343000] usb 5-8: device descriptor read/64, error -71
[4294798.546000] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[4294803.558000] usb 5-8: device descriptor read/8, error -110

```

---

### Post by escobar5 on 2006-06-06
I GOT IT WORKING!!!!!

after a long time looking for a solution, i found this line in another thread that solved my problem:
```

 sudo modprobe -r ehci_hcd

```

I don't know why it works, but it did.

the thread was this: [http://ubuntuforums.org/showthread.php?t=48126&highlight=ipod+mount+problem](http://ubuntuforums.org/showthread.php?t=48126&highlight=ipod+mount+problem)

and this was the explanation:
```
once you plug the disk while you are already in gnome. In that way, you remove the module

ehci_hcd

and the module

ohci_hcd

handles the disk automounting process:
```

---

