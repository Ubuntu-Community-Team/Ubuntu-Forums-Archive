---
title: "Perixx Periboard-520 Wired Trackball Keyboard - trackball not working"
date: 2020-07-12
forum: Hardware
---

### Post by raidensix2 on 2020-07-12
[SIZE=2][FONT=microsoft sans serif][/FONT][/SIZE][SIZE=3]Hi, is anyone using or has managed to get the Perrix Periboard-520 Wired Trackball Keyboard working 100%?

I only get the keyboard working and based on the logs, Ubuntu 20.04 seems to think the trackball is an MTP device:

==========
[/SIZE][COLOR=#000000][FONT=Menlo]ul 12 14:08:08 raiden-nas kernel: [403535.158715] usb 3-9: new low-speed USB device number 2 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.319326] usb 3-9: New USB device found, idVendor=04d9, idProduct=a1f1, bcdDevice= 1.15[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.319332] usb 3-9: New USB device strings: Mfr=0, Product=0, SerialNumber=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas mtp-probe: bus: 3, device: 2 was not an MTP device[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.345788] hidraw: raw HID events driver (C) Jiri Kosina[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.356599] usbhid 3-9:1.1: can't add hid device: -22[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.356613] usbhid: probe of 3-9:1.1 failed with error -22[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.356623] usbcore: registered new interface driver usbhid[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas kernel: [403535.356624] usbhid: USB HID core driver[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul 12 14:08:08 raiden-nas mtp-probe: bus: 3, device: 2 was not an MTP device[/FONT][/COLOR]
=============

Any help, appreciated!

---

### Post by dougkerr on 2020-10-04
Raidensix2, did you ever get the trackball working on the periboard-520? I have the same problem. Thanks

---

