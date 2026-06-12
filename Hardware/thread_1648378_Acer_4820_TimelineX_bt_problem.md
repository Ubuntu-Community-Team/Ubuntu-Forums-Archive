---
title: "Acer 4820 TimelineX bt problem"
date: 2010-12-18
forum: Hardware
---

### Post by Xanfer on 2010-12-18
Hi,
After install Ubuntu on Acer 4820tg i got some trouble with Bluetooth

It seems that when i  boot to Ubuntu after windows(laptop is turned off with working bt) it works quite well until i disable it by Fn+F3 .
But if i try to use bt again it get enabled only for 1 or 2 seconds after pressing  Fn+F3 

dmesg write:
```
[ 2282.133960] usb 2-1.5: new full speed USB device using ehci_hcd and address 4
[ 2282.340781] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[ 2282.640335] usbcore: registered new interface driver ath3k
[ 2282.842783] usb 2-1.5: USB disconnect, address 4
[ 2284.102956] usb 2-1.5: new full speed USB device using ehci_hcd and address 5
[ 2284.260696] Bluetooth: Core ver 2.15
[ 2284.260734] NET: Registered protocol family 31
[ 2284.260737] Bluetooth: HCI device and connection manager initialized
[ 2284.260741] Bluetooth: HCI socket layer initialized
[ 2284.265246] Bluetooth: Generic Bluetooth USB driver ver 0.6
[ 2284.265767] usbcore: registered new interface driver btusb
[ 2284.327553] Bluetooth: L2CAP ver 2.14
[ 2284.327560] Bluetooth: L2CAP socket layer initialized
[ 2284.357449] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 2284.357455] Bluetooth: BNEP filters: protocol multicast
[ 2284.369643] Bluetooth: SCO (Voice Link) ver 0.6
[ 2284.369649] Bluetooth: SCO socket layer initialized
[ 2284.633699] usb 2-1.5: USB disconnect, address 5
[ 2284.633724] btusb_intr_complete: hci0 urb ffff8801245da000 failed to resubmit (19)
[ 2284.633971] btusb_bulk_complete: hci0 urb ffff8801245da300 failed to resubmit (19)
[ 2284.633977] btusb_bulk_complete: hci0 urb ffff8801245daa80 failed to resubmit (19)
[ 2284.635551] hub 2-1:1.0: hub_port_status failed (err = -32)
[ 2284.635560] hub 2-1:1.0: connect-debounce failed, port 5 disabled

```

rfkill event shows
```

1292709934.985283: idx 0 type 1 op 0 soft 0 hard 0
1292709939.736069: idx 1 type 2 op 0 soft 0 hard 0
1292709939.736132: idx 1 type 2 op 2 soft 0 hard 0
1292709940.104787: idx 1 type 2 op 1 soft 0 hard 0

```

---

### Post by opticron on 2010-12-23
I have this exact same problem with debian sid on my 3820T.  It prevents me from using bluetooth at all, but I am also using a backported driver with 2.6.32 (when I think the driver was merged in 2.6.34).

---

### Post by Xanfer on 2011-01-13
Arch linux wiki for TimelineX helped with this: 
> 
Symptoms include "usb disconnect" messages in dmesg, and the adapter not showing up in hcitool dev.) In this case, copying /lib/firmware/ath3k-2.fw to /lib/firmware/ath3k-1.fw helps


---

