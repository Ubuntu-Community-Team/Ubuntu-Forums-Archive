---
title: "usb charging wakes up phone continously"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by wsw70 on 2008-01-29
Greetings,

I run ubuntu on my server and (blind of the obvious) I decided to use it also to recharge my phone (a Motorola Q). It essentially works out of the box, except that the phone wakes up every minutes (the screen gets gright, or the phone switches on when it was off).

The device seems to be recognized properly: 
```
Bus 001 Device 066: ID 22b8:4221 Motorola PCS
```

dmesg however shows that it is being connected and disconnected continuously:
```
root@ns:~# dmesg | tail
[57060.543665] usb 1-2: USB disconnect, address 65
[57060.543776] eth2: unregister 'rndis_host' usb-0000:00:1d.0-2, RNDIS device
[57063.085859] usb 1-2: new full speed USB device using uhci_hcd and address 66
[57063.268406] usb 1-2: configuration #1 chosen from 1 choice
[57063.356125] eth2: register 'rndis_host' at usb-0000:00:1d.0-2, RNDIS device, 80:00:94:7c:61:9e
[57124.368445] usb 1-2: USB disconnect, address 66
[57124.368554] eth2: unregister 'rndis_host' usb-0000:00:1d.0-2, RNDIS device
[57126.910643] usb 1-2: new full speed USB device using uhci_hcd and address 67
[57127.093181] usb 1-2: configuration #1 chosen from 1 choice
[57127.180910] eth2: register 'rndis_host' at usb-0000:00:1d.0-2, RNDIS device, 80:00:94:7c:61:9e
```

If there is no solution (or worse - if this is expected behaviour) -- is there a way to disable most of the functionality of a given USB port and just keep the power feature (it would be used for this purpose only).

Thanks in advance for any pointers,
Wojtek

---

### Post by oldsoundguy on 2008-01-29
may be way off here, but IF I remember correctly, the majority of USB functions are chipset regulated and the OS just "recognizes" the unit. (why WinDOZE dumps USB items all the time .. has amnesia!)

I don't use the USB to charge my PDA .. I disconnect it when I need to charge it and put it in a charging cradle.   It may be a convenient thing for you to try and use the computer, but believe they really weren't meant to be charged that way.

---

### Post by wsw70 on 2008-01-30
> **oldsoundguy said:**
> I don't use the USB to charge my PDA .. I disconnect it when I need to charge it and put it in a charging cradle.   It may be a convenient thing for you to try and use the computer, but believe they really weren't meant to be charged that way.

I would be delighted to do the same -- but I have mislocated the charger (duh) and this is a micro-USB one (which means I have to go to a shop to get one as the 15 other I have are mini-USB ... yes I know this is a lame excuse).

Please note that the diconnections are due to a new ethX being cretaed and istroyed in a cycle. So it would be a matter of explaining to the system not to try to do networking on that USB (or even on USB all together)

Thanks,
Wojtek

---

