---
title: "microsoft mouse stops working after hours/days/weeks"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by timgrin on 2008-03-18
OS: Ubuntu 7.10
Uname: Linux eli 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

I have an ubuntu server/desktop computer that the microsoft usb mouse stops working (ie light goes out and buttons/scroller stop working) after any period of time.

When I plug the mouse into another usb port it lights up and goes again - however the dead usb port won't start until a reboot.

I have tried as mentioned by some launchpad and forum entries:

```
 
sudo modprobe -r ehci_hcd
sudo modprobe  ehci_hcd
sudo modprobe -r ohci_hcd
sudo modprobe ohci_hcd no_handshake=1

```

[LIST]
[*]Bug #84762
[*]Bug #70008
[*]Bug #184382
[/LIST]

My dmesg reads as follows - this is after port stops working and I plug into another:

```

[1033602.968000] usb 2-1: new low speed USB device using uhci_hcd and address 4
[1033603.148000] usb 2-1: configuration #1 chosen from 1 choice
[1033603.164000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input9
[1033603.164000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-1
[1033603.748000] usb usb3: Controller not stopped yet!
[1033935.364000] usb 2-1: USB disconnect, address 4
[1033936.360000] usb 2-1: new low speed USB device using uhci_hcd and address 5
[1033952.100000] usb 4-1: new low speed USB device using uhci_hcd and address 3
[1033952.280000] usb 4-1: configuration #1 chosen from 1 choice
[1033952.300000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input10
[1033952.300000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.3-1
[1033952.752000] usb usb2: Controller not stopped yet!
[1034314.172000] ehci_hcd 0000:00:10.4: remove, state 4
[1034314.172000] usb usb5: USB disconnect, address 1
[1034314.180000] ehci_hcd 0000:00:10.4: USB bus 5 deregistered
[1034314.180000] ACPI: PCI interrupt for device 0000:00:10.4 disabled
[1035188.668000] usb 4-1: USB disconnect, address 3
[1035196.304000] usb 3-1: new low speed USB device using uhci_hcd and address 6
[1035211.552000] usb 3-1: device descriptor read/64, error -110
[1035226.924000] usb 3-1: device descriptor read/64, error -110
[1035227.140000] usb 3-1: new low speed USB device using uhci_hcd and address 7
[1035237.360000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[1035242.548000] usb 3-1: device descriptor read/64, error -110
[1035257.920000] usb 3-1: device descriptor read/64, error -110
[1035258.136000] usb 3-1: new low speed USB device using uhci_hcd and address 8
[1035268.848000] usb 3-1: device not accepting address 8, error -110
[1035268.960000] usb 3-1: new low speed USB device using uhci_hcd and address 9
[1035279.684000] usb 3-1: device not accepting address 9, error -110
[1035281.692000] usb usb3: Controller not stopped yet!
[1035318.692000] usb 3-1: new low speed USB device using uhci_hcd and address 10
[1035319.496000] usb usb2: Controller not stopped yet!
[1035334.052000] usb 3-1: device descriptor read/64, error -110
[1035349.424000] usb 3-1: device descriptor read/64, error -110
[1035349.640000] usb 3-1: new low speed USB device using uhci_hcd and address 11
[1035365.048000] usb 3-1: device descriptor read/64, error -110
[1035380.420000] usb 3-1: device descriptor read/64, error -110
[1035380.636000] usb 3-1: new low speed USB device using uhci_hcd and address 12
[1035391.348000] usb 3-1: device not accepting address 12, error -110
[1035391.460000] usb 3-1: new low speed USB device using uhci_hcd and address 13
[1035402.184000] usb 3-1: device not accepting address 13, error -110
[1035404.192000] usb usb3: Controller not stopped yet!
[1035407.136000] usb 3-1: new low speed USB device using uhci_hcd and address 14
[1035407.940000] usb usb2: Controller not stopped yet!
[1035422.496000] usb 3-1: device descriptor read/64, error -110
[1035437.780000] usb usb2: Controller not stopped yet!
[1035437.868000] usb 3-1: device descriptor read/64, error -110
[1035438.084000] usb 3-1: new low speed USB device using uhci_hcd and address 15
[1035453.496000] usb 3-1: device descriptor read/64, error -110
[1035468.868000] usb 3-1: device descriptor read/64, error -110
[1035469.084000] usb 3-1: new low speed USB device using uhci_hcd and address 16
[1035479.796000] usb 3-1: device not accepting address 16, error -110
[1035479.908000] usb 3-1: new low speed USB device using uhci_hcd and address 17
[1035490.632000] usb 3-1: device not accepting address 17, error -110
[1035492.640000] usb usb3: Controller not stopped yet!
[1035574.856000] usb usb3: Controller not stopped yet!
[1035578.256000] usb 4-1: new low speed USB device using uhci_hcd and address 4
[1035578.436000] usb 4-1: configuration #1 chosen from 1 choice
[1035578.456000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input11
[1035578.456000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.3-1


```

Any help would be appreciated.

---

### Post by erginemr on 2008-03-19
If your mouse kills this second usb port as well after a while, I might start suspecting the mouse itself. You said it was microsoft made? ;)

Not a solution really, but if you cannot find a solution to this problem, you may consider using a cheap ps2-to-usb adapter (such as [http://sewelldirect.com/ps2tousb.asp](http://sewelldirect.com/ps2tousb.asp)) that are commonly sold in computer shops, if you happen to have a ps2 slot at the back of your box.

---

