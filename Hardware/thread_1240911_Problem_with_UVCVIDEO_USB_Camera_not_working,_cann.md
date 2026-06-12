---
title: "Problem with UVCVIDEO: USB Camera not working, cannot get freq at ep 0x84"
date: 2009-08-15
forum: Hardware
---

### Post by cryinstone on 2009-08-15
Hi,
My USB camera does not work:

dmitry@justice:~$ lsusb
Bus 001 Device 005: ID 04f2:a133 Chicony Electronics Co., Ltd Gateway Webcam

dmitry@justice:~$ dmesg | tail
[  685.032024] usb 1-7: new high speed USB device using ehci_hcd and address 4
[  685.193810] usb 1-7: configuration #1 chosen from 1 choice
[  685.236557] 4:3:1: cannot get freq at ep 0x84
[  685.281216] uvcvideo: Found UVC 1.00 device USB2.0 1.3MP UVC Camera (04f2:a133)
[  685.289323] input: USB2.0 1.3MP UVC Camera as /devices/pci0000:00/0000:00:10.4/usb1/1-7/1-7:1.0/input/input9
[  685.324784] usbcore: registered new interface driver uvcvideo
[  685.324793] USB Video Class driver (v0.1.0)
[  686.038747] 4:3:1: cannot get freq at ep 0x84

dmitry@justice:~$ uname -r
2.6.28-14-generic

I did dowload, compile & install latest uvcvideo, but the problem is NOT solved.
Any ideas?

---

