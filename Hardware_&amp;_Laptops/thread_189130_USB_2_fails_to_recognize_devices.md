---
title: "USB 2 fails to recognize devices"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by tarkus on 2006-06-04
I'm having trouble with my EHCI controller - USB 1 devices (eg printer) work great, but any device that supports 2 dies with messages like the following:
> Jun  4 17:33:34 localhost kernel: [ 1363.209950] usb 1-4: new high speed USB device using ehci_hcd and address 7
Jun  4 17:33:36 localhost kernel: [ 1365.099454] usb 1-4: device descriptor read/64, error -110
Jun  4 17:33:46 localhost kernel: [ 1370.712972] usb 1-4: device descriptor read/64, error -110
Jun  4 17:33:46 localhost kernel: [ 1370.821322] usb 1-4: new high speed USB device using ehci_hcd and address 8
Jun  4 17:33:48 localhost kernel: [ 1371.874978] usb 1-4: device descriptor read/64, error -110
Jun  4 17:33:59 localhost kernel: [ 1376.969187] usb 1-4: device descriptor read/64, error -110
Jun  4 17:33:59 localhost kernel: [ 1377.070544] usb 1-4: new high speed USB device using ehci_hcd and address 9
Jun  4 17:34:09 localhost kernel: [ 1382.888597] usb 1-4: device not accepting address 9, error -110
Jun  4 17:34:09 localhost kernel: [ 1382.939343] usb 1-4: new high speed USB device using ehci_hcd and address 10
Jun  4 17:34:14 localhost kernel: [ 1385.441880] usb 1-4: device descriptor read/8, error -110
Jun  4 17:34:20 localhost kernel: [ 1387.994250] usb 1-4: device descriptor read/8, error -110

I have the following controller:
> 0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1c05
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1c05
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

I can find no reference to error -110 in this context, and this is getting very frustrating.  Any ideas or places to check for help?  Thanks!
Steven

---

### Post by tarkus on 2006-06-05
I upgraded to the latest kernel (2.6.16.19) and now it produces this error instead:
> Jun  5 16:56:25 localhost kernel: [ 2836.422181] usb 1-3: khubd timed out on ep0in len=0/64
Jun  5 16:56:25 localhost kernel: [ 2836.447710] ehci_hcd 0000:00:02.1: port 3 high speed
Jun  5 16:56:25 localhost kernel: [ 2836.447715] ehci_hcd 0000:00:02.1: GetStatus port 3 status 001005 POWER sig=se0 PE CONNECT
Jun  5 16:56:25 localhost kernel: [ 2836.473051] usb 1-3: device descriptor read/64, error -110
Jun  5 16:56:26 localhost kernel: [ 2836.549057] ehci_hcd 0000:00:02.1: port 3 high speed
Jun  5 16:56:26 localhost kernel: [ 2836.549063] ehci_hcd 0000:00:02.1: GetStatus port 3 status 001005 POWER sig=se0 PE CONNECT
Jun  5 16:56:26 localhost kernel: [ 2836.574411] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jun  5 16:56:31 localhost kernel: [ 2839.076941] usb 1-3: khubd timed out on ep0in len=0/8
Jun  5 16:56:31 localhost kernel: [ 2839.076946] usb 1-3: device descriptor read/8, error -110
Jun  5 16:56:36 localhost kernel: [ 2841.629392] usb 1-3: khubd timed out on ep0in len=0/8
Jun  5 16:56:36 localhost kernel: [ 2841.629397] usb 1-3: device descriptor read/8, error -110
Jun  5 16:56:36 localhost kernel: [ 2841.705343] ehci_hcd 0000:00:02.1: port 3 high speed
Jun  5 16:56:36 localhost kernel: [ 2841.705349] ehci_hcd 0000:00:02.1: GetStatus port 3 status 001005 POWER sig=se0 PE CONNECT
Jun  5 16:56:36 localhost kernel: [ 2841.730712] usb 1-3: new high speed USB device using ehci_hcd and address 5
Jun  5 16:56:41 localhost kernel: [ 2844.227284] usb 1-3: khubd timed out on ep0out len=0/0
Jun  5 16:56:41 localhost kernel: [ 2844.327654] ehci_hcd 0000:00:02.1: devpath 3 ep0out 3strikes
Jun  5 16:56:41 localhost kernel: [ 2844.427937] usb 1-3: device not accepting address 5, error -71
Jun  5 16:56:41 localhost kernel: [ 2844.427952] hub 1-0:1.0: state 7 ports 10 chg 0000 evt 0008

---

### Post by tarkus on 2006-06-05
I tried updating my BIOS and that seems to have fixed it... no clue why though.

---

