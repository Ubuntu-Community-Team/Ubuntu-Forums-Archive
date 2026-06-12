---
title: "Why my portable hard drive does not work?"
date: 2009-01-06
forum: Hardware
---

### Post by emmanuel.brasil on 2009-01-06
Hi all,

I looked for in many foruns and google it several times but I didnt find any solution so far. 

O got as a gift a Iomega 250GB portable hard drive. However when a stick in the USB into the PC... nothing happens. That is ... no icon appears at the desktop as expected neither anything appears at the nautilus tree. 

Latter I found out that Iomega does not give support to linux (this device has drives only for win and mac). 

Than I dicided to look for a generic drive that could make it work. But so far... no solution at all.

Does anyone have a tip to make it work?

Thanks in andvance!
Best regards!

---

### Post by cariboo on 2009-01-06
You should need drivers, as most Iomega devices are supported out of the box. In a Applications-->Accessories--Terminal type the following when you plug your device in:

```
dmesg | tail -n10
```

and paste the output in your next post.

Jim

---

### Post by arschenk on 2009-01-07
I have this same exact problem with the same hard drive.  Following your instructions, the terminal reads:

andrew@andrew-desktop:~$ dmesg | tail -n10
[   31.134398] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   31.630310] NET: Registered protocol family 17
[   33.280935] NET: Registered protocol family 10
[   33.282159] lo: Disabled Privacy Extensions
[  122.806533] ppdev0: registered pardevice
[  122.853376] ppdev0: unregistered pardevice
[  124.424648] ppdev0: registered pardevice
[  124.472241] ppdev0: unregistered pardevice
[  124.556201] ppdev0: registered pardevice
[  124.604035] ppdev0: unregistered pardevice

---

### Post by arschenk on 2009-01-07
mine ended up working - just tried a different usb port, thanks!

---

### Post by emmanuel.brasil on 2009-01-07
Well... after the the third post I tried to some different stuff at the USB ports. 

It happens that my PC has no USB at the front and four at the back. One is busy with the printer, one with the webcam, one with the mouse and one has an extesion with a hub with four USB ports. So, the two USB cables from the hard drive were at the USB hub, that is at a single PC USB port.

What I tried was to take out the webcam and stick it into the USB hub. Later I put another one simple extension where the webcam was. Than, I sticked the portable hard drive in two different USB ports, the first at the USB hub and the second directly into the computer.

With this it seems to work fine.

So it seems that it was not a problem related to the device drive, but related the electric power available from one or two USB port to make the device run correctly.

Anyway here is the output from the terminal command:

> dmesg | tail -n10
[  209.899853] Bluetooth: L2CAP ver 2.9
[  209.899866] Bluetooth: L2CAP socket layer initialized
[  210.056911] Bluetooth: RFCOMM socket layer initialized
[  210.057611] Bluetooth: RFCOMM TTY layer initialized
[  210.057628] Bluetooth: RFCOMM ver 1.8
[  211.576999] eth0: Media Link On 100mbps full-duplex 
[  212.312733] NET: Registered protocol family 17
[  219.006637] NET: Registered protocol family 10
[  219.008085] lo: Disabled Privacy Extensions
[  229.966683] eth0: no IPv6 routers present

Thanks for the attention... it helped me to think on a work around to my problem!

Best regards to all!

---

