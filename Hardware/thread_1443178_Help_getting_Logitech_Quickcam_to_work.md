---
title: "Help getting Logitech Quickcam to work"
date: 2010-03-30
forum: Hardware
---

### Post by pk_vex on 2010-03-30
Hi,

I searched on google and confirmed that ubuntu version 7.x worked with my webcam using the gspca.  The hardware ID is 0x092E.

However, my current ubuntu version of 9.1 doesn't work.  Both Cheese, and a webcam test website doesn't detect my webcam at all.  The webcam LED just stays on all the time.

I'm not too sure where to go from here.  

The following is the output from my dmesg:


```

[  379.258822] usb 2-1: USB disconnect, address 2
[  379.259136] gspca: disconnect complete
[  382.812180] usb 2-1: new full speed USB device using ohci_hcd and address 3
[  383.354458] usb 2-1: configuration #1 chosen from 1 choice
[  383.362122] gspca: probing 046d:092e
[  383.682382] gspca: probe ok

```

---

### Post by pk_vex on 2010-03-31
top,

anyone?  I'm using Virtualbox, though I don't know if this makes any difference.  I've also tried a different webcam as well, and still the same results.  

The following is the dmsg for the new webcam I tested.

```
[   93.096880] usb 2-1: configuration #1 chosen from 1 choice
[   93.252528] Linux video capture interface: v2.00
[   93.264697] gspca: main v2.6.0 registered
[   93.283377] STV06xx: Probing for a stv06xx device
[   93.283380] gspca: probing 046d:08f0
[   93.283387] STV06xx: Configuring camera
[   93.283388] STV06xx: st6422 sensor detected
[   93.283389] STV06xx: Initializing camera
[   93.340211] quickcam_messenger: v0.01:Logitech Quickcam Messenger USB
[   93.725552] gspca: probe ok
[   93.725593] STV06xx: Probing for a stv06xx device
[   93.725595] gspca: probing 046d:08f0
[   93.725629] STV06xx: Probing for a stv06xx device
[   93.725631] gspca: probing 046d:08f0
[   93.725651] usbcore: registered new interface driver STV06xx
[   93.725653] STV06xx: registered
[   93.726546] usbcore: registered new interface driver QCM
[   93.964864] usbcore: registered new interface driver snd-usb-audio

```

---

### Post by cariboo on 2010-03-31
Which version of Virtualbox have you got installed? The version from the repositories or from Virtualbox? Do you have the Guest Additions installed?

Your webcam works by default in a regular install.

---

