---
title: "Durabrand SF-MW205 Wireless Rechargeable Optical Mouse"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by centyx on 2007-05-28
Picked up the Durabrand SF-MW205 "Wireless Rechargeable Optical Mouse" from Wal Mart for $20. I can't seem to get the mouse to work w/ Xorg or gpm.  

lshw reports this for the device:

              *-usb
                   description: Mouse
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s

dmesg shows
 
[56150.889901] usb 2-2: new low speed USB device using uhci_hcd and address 4
[56151.044552] usb 2-2: configuration #1 chosen from 1 choice
[56151.060532] input: HID 062a:0000 as /class/input/input7
[56151.060593] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.1-2

Does anyone else have this mouse? Any suggestions would be greatly appreciated.

- Michael

---

### Post by centyx on 2007-10-27
I returned this mouse to Wal Mart the week following the original post because I could not get it to work.

I see on the OpenSuse mailing list that someone got it to work, but no details were given.

I am now wondering about the HP ( Micro Innovations ) PP034AA sold at Wal Mart and Comp USA, also a wireless mouse with charger.

---

