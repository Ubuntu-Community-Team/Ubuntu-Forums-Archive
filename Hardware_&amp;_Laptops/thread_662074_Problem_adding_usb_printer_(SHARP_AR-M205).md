---
title: "Problem adding usb printer (SHARP AR-M205)"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by leo_br on 2008-01-08
Hello,

I am trying to get an SHARP AR-M205 to work with Ubuntu Gutsy.
If I connect the printer straight to my laptop I get a series of the following message:


Jan  8 18:57:05 LJ kernel: [  561.556000] usb 2-3: new full speed USB device using ohci_hcd and address 7
Jan  8 18:57:05 LJ NetworkManager: <debug> [1199807825.704277] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4dd_9004_0000040621104217'). 
Jan  8 18:57:05 LJ kernel: [  561.816000] usb 2-3: configuration #1 chosen from 1 choice
Jan  8 18:57:05 LJ kernel: [  561.864000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 7 if 1 alt 0 proto 2 vid 0x04DD pid 0x9004
Jan  8 18:57:05 LJ NetworkManager: <debug> [1199807825.895479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jan  8 18:57:05 LJ kernel: [  562.064000] usb 2-3: USB disconnect, address 7
Jan  8 18:57:05 LJ kernel: [  562.068000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -62

Sharing this printer from  Windows and trying to print from Ubuntu through Samba, also without success. The job is received by Windows and after some seconds just disappears.

Any suggestions?
Thanks in advance!

---

### Post by leo_br on 2008-01-09
Bump! Anybody?

---

### Post by leo_br on 2008-01-12
Any ideas? Suggestions?

---

### Post by RevNomad on 2008-01-17
Experiencing a similar problem.  Ubuntu on a Compaq Presario SR1211NX cannot find the printer.:mad:

---

