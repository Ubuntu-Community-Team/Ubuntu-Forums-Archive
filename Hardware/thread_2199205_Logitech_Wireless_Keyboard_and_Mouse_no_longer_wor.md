---
title: "Logitech Wireless Keyboard and Mouse no longer working"
date: 2014-01-12
forum: Hardware
---

### Post by inhumangeek on 2014-01-12
I have the Logitech LX 710 wireless keyboard about mouse. This has been working happily straight out of the box with no configuration required. However some months ago both the keyboard and mouse stopped working, so I assumed the receiver has packed up and put them away at the back of a cupboard. I then tested them yesterday on a Windows laptop and they work fine! I therefore conclude that some upgrade in Ubuntu has caused them to stop working; it could have been when I upgraded to 13.04. 

I have had a look around and others are having similar problems with their Logitech keyboards/mice, but they use the "Unifying Receiver", which I don't have (or at least I don't think I have!). One post [here]("http://askubuntu.com/questions/311653/logitech-wireless-m525-mouse-not-working-on-ubuntu-13-04") asks for the output of the syslog, so here's mine:
 
sudo tail -f -n 0 /var/log/syslog

```
Jan 12 21:28:47 deepthought kernel: [19584.006435] usb 5-2.1: new low-speed USB device number 19 using xhci_hcd
Jan 12 21:28:48 deepthought kernel: [19584.032685] usb 5-2.1: New USB device found, idVendor=046d, idProduct=c517
Jan 12 21:28:48 deepthought kernel: [19584.032691] usb 5-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan 12 21:28:48 deepthought kernel: [19584.032694] usb 5-2.1: Product: USB Receiver
Jan 12 21:28:48 deepthought kernel: [19584.032697] usb 5-2.1: Manufacturer: Logitech
Jan 12 21:28:48 deepthought kernel: [19584.032863] usb 5-2.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan 12 21:28:48 deepthought kernel: [19584.032868] usb 5-2.1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan 12 21:28:48 deepthought kernel: [19584.036920] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1c.5/0000:06:00.0/usb5/5-2/5-2.1/5-2.1:1.0/input/input30
Jan 12 21:28:48 deepthought kernel: [19584.037114] logitech 0003:046D:C517.0012: input,hidraw3: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:06:00.0-2.1/input0
Jan 12 21:28:48 deepthought kernel: [19584.042010] logitech 0003:046D:C517.0013: fixing up Logitech keyboard report descriptor
Jan 12 21:28:48 deepthought kernel: [19584.042282] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1c.5/0000:06:00.0/usb5/5-2/5-2.1/5-2.1:1.1/input/input31
Jan 12 21:28:48 deepthought kernel: [19584.042562] logitech 0003:046D:C517.0013: input,hiddev0,hidraw4: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:06:00.0-2.1/input1
Jan 12 21:28:48 deepthought mtp-probe: checking bus 5, device 19: "/sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/usb5/5-2/5-2.1"
Jan 12 21:28:48 deepthought mtp-probe: bus: 5, device: 19 was not an MTP device
```

lsusb

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 009: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 010: ID 047d:2043 Kensington 
Bus 005 Device 018: ID 0971:2005 Gretag-Macbeth AG Huey
Bus 005 Device 019: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 002: ID 03f0:2f24 Hewlett-Packard LP2475w Monitor Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

[This post]("http://askubuntu.com/questions/237029/logitech-wireless-m510-does-not-work-12-10") suggests something happened at 12.10 upgrade.
 
**UPDATE:**

[FONT=courier new]sudo modprobe -r hid_logitech_dj && modprobe hid_logitech_dj[/FONT]  seems to work, sometimes... but then again the receiver isn't always being picked up in lsusb - I have to plug and unplug a few times into different sockets. Once it is found in lsusb, the modprobe then works. Most annoying! I have put the two modprobe commands into init.d as a script (as suggested [here]("http://askubuntu.com/questions/128345/logitech-m515-does-not-work-after-upgrade-to-12-04?rq=1")) but as the receiver isn't always being picked up, this is not reliable. Is there a way to avoid have to unplug and replug?

Any advice or pointers most welcome. Many thanks.

---

### Post by inhumangeek on 2014-01-12
After a lot of fiddling I have found that the USB plug on the receiver is loose where it is connected onto the circuit board. If I hold the receiver to one side it works. It has a 5 year warranty so I have contacted Logitech support.
Not sure whether the modprobe is required after all!

---

