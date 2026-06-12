---
title: "No usb working"
date: 2008-08-07
forum: Hardware
---

### Post by hybrider on 2008-08-07
hi,
I've tried different mouses and memory sticks but nothing works. It seems like if they not even get power because the device's lights dont turn on.
lsusb shows:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

any ideas how i can get it working?

---

### Post by hybrider on 2008-08-07
maybe this will help a expert to understand my problem:
dmesg | grep -i hci shows:
[   16.037885] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.037970] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.038319] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.038347] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0404000
[   16.195377] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.195404] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   16.195424] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0405000
[   16.355480] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   16.355511] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   16.355572] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0406000
[   16.367203] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.708820] Bluetooth: HCI device and connection manager initialized
[   39.708825] Bluetooth: HCI socket layer initialized
[  373.753890] usb 3-1: new high speed USB device using ehci_hcd and address 2
[  373.811921] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  374.015786] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  374.219680] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  374.423521] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  374.627372] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  374.683343] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  374.887198] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  375.091071] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  375.294898] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  375.498751] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  375.554712] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  375.758561] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  375.962414] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  376.166285] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  376.370126] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  376.426077] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  376.629931] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  376.833790] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  377.037626] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  377.241507] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  395.336048] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  395.574215] usb 3-7: new high speed USB device using ehci_hcd and address 6
[  396.117833] usb 3-7: new high speed USB device using ehci_hcd and address 7
[  396.661430] usb 3-7: new high speed USB device using ehci_hcd and address 8
[  397.181060] usb 3-7: new high speed USB device using ehci_hcd and address 9
[  397.594442] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  597.542797] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  597.694688] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  600.248855] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  600.487023] usb 3-5: new high speed USB device using ehci_hcd and address 10
[  601.030623] usb 3-5: new high speed USB device using ehci_hcd and address 11
[  601.574221] usb 3-5: new high speed USB device using ehci_hcd and address 12
[  602.093864] usb 3-5: new high speed USB device using ehci_hcd and address 13
[  602.507258] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  934.917731] ehci_hcd 0000:00:13.2: port 1 resume error -110
[  935.069686] ehci_hcd 0000:00:13.2: port 1 resume error -110
[ 1177.757080] ehci_hcd 0000:00:13.2: port 1 resume error -110
[ 1332.438972] ehci_hcd 0000:00:13.2: port 1 resume error -110

---

### Post by hybrider on 2008-08-07
anyone?

---

