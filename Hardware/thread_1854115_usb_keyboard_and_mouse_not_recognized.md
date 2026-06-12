---
title: "usb keyboard and mouse not recognized"
date: 2011-10-03
forum: Hardware
---

### Post by basantk on 2011-10-03
Hi,
   I have a Sun Desktop (x86_64, amd opteron) system. I have been running several versions of Fedora on this box for long time. I wanted to switch to Ubuntu natty (11.04). I have been able to install ubuntu from usb pen drive however I have a serious issue with the keyboard and mouse. Neither the keyboard nor mouse are recognized so I can't do anything with the system after ubuntu boots.
* I have not been able to configure network so I can't do ssh to it. I can ping the machine but can't login to it.
* System don't have any ps2 keyboard support so I can't use any ps2 keyboard either.

Here are the things which I tried :
* System was able to recognize keyboard/mouse once (lucky). In that case syslog contains the following entry :
Oct  3 11:52:12 hostname kernel: [    2.940389] generic-usb 0003:0557:2213.0001: input,hidraw0: USB HID v1.00 Keyboard [ATEN CS-1734 V1.0.091] on usb-0000:01:03.0-1.3/input0

So it seems like usbhid driver loads it.
* I tried using the following boot options one by one but none of them helped.
usb, usbhid, noapic, acpi=off, nolapic, edd=on, nodmraid
* When I see the following in syslog (from fedora boot) (grep -i usb syslog)
Oct  3 14:17:47 hostname kernel: [    0.042392] usbcore: registered new interface driver usbfs
Oct  3 14:17:47 hostname kernel: [    0.042469] usbcore: registered new interface driver hub
Oct  3 14:17:47 hostname kernel: [    0.042555] usbcore: registered new device driver usb
Oct  3 14:17:47 hostname kernel: [    0.175412] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct  3 14:17:47 hostname kernel: [    0.175497] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct  3 14:17:47 hostname kernel: [    0.180430] ohci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 1
Oct  3 14:17:47 hostname kernel: [    0.242315] hub 1-0:1.0: USB hub found
Oct  3 14:17:47 hostname kernel: [    0.250426] ohci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 2
Oct  3 14:17:47 hostname kernel: [    0.312345] hub 2-0:1.0: USB hub found
Oct  3 14:17:47 hostname kernel: [    0.312603] uhci_hcd: USB Universal Host Controller Interface driver
Oct  3 14:17:47 hostname kernel: [   26.771987] usbcore: registered new interface driver usbhid
Oct  3 14:17:47 hostname kernel: [   26.771990] usbhid: USB HID core driver
Oct  3 14:17:47 hostname kernel: [   26.874177] Initializing USB Mass Storage driver...
Oct  3 14:17:47 hostname kernel: [   26.874444] usbcore: registered new interface driver usb-storage
Oct  3 14:17:47 hostname kernel: [   26.874446] USB Mass Storage support registered.

* I booted the system in rescue mode but have the same issue (so it is not a gdm issue)
* I have 2 kernels installed 2.6.38-8 and 2.6.38-11, both have the same results.
* I enabled all usb drivers in /etc/modules e.g. "usb, usbhid, usb-storage" but no use.
* I commented usbmouse and usbkbd in blacklist.conf in /etc/modprobe.d/blacklist.conf but still no luck.
* I have reinstalled ubuntu 2nd time but still no luck.

---

