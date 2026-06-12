---
title: "hotplug wacom tablet"
date: 2008-08-31
forum: Hardware
---

### Post by mooseydoom on 2008-08-31
Wondering if anyone has had any success hotplugging their wacom tablet?

My graphire 4 works if it is plugged in when Ubuntu is started up (or when logging in), but if I unplug it and plug it back in, the tablet goes back to acting like a mouse (using the generic hid driver instead of the wacom driver).  I've tried installing wdaemon, but it doesn't activate the wacom driver.

How can I get the tablet to use the wacom driver when it is plugged in?

dmesg output, showing the wacom driver being used on startup, but using the HID driver when being replugged.
```
[   64.118921] input: uinput: Wacom Graphire4 4x5 as /devices/virtual/input/input9
[   64.971330] usbcore: registered new interface driver wacom
[   64.971339] /build/buildd/linux-2.6.24/drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver
[   77.328637] NET: Registered protocol family 10
[   77.329243] lo: Disabled Privacy Extensions
[   77.329985] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   87.490049] ath0: no IPv6 routers present
[   97.261561] NET: Registered protocol family 17
[  107.575665] gnome-panel[14958]: segfault at 000000a6 eip b22efb19 esp b2b5a66c error 4
[  116.371324] ath0: no IPv6 routers present
[  124.863362] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  126.891911] usb 3-1: new low speed USB device using uhci_hcd and address 2
[  127.066137] usb 3-1: configuration #1 chosen from 1 choice
[  127.071974] input: Wacom Graphire4 4x5 as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input10
[  127.178231] usbcore: registered new interface driver hiddev
[  127.178512] usbcore: registered new interface driver usbhid
[  127.178657] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

```

---

### Post by ceti331 on 2008-08-31
i get the same. Hotplugging at all was a step forward, but it reverts to mouse-like behaviour unless it's seen at startup for me.
Prior to ubuntu 8 i basically had to edit Xorg.conf to prevent it CRASHING if you try and boot without a tablet plugged in :)

---

### Post by mooseydoom on 2008-08-31
Looks like I might have to wait for Intrepid's input hotplugging

---

