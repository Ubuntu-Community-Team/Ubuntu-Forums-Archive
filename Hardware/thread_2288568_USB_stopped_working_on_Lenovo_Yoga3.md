---
title: "USB stopped working on Lenovo Yoga3"
date: 2015-07-28
forum: Hardware
---

### Post by tomcat3 on 2015-07-28
Hi,
I have a serious problem with with my USB ports, they suddenly stopped working over night. They do not have any power, not even during the boot process.

I already tried 

echo "on" | sudo tee /sys/bus/usb/devices/usb*/power/control

I also resetted BIOS. No result.

Who can help?

uname -a

> Linux cc 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


lsusb

> Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 5986:0535 Acer, Inc 
Bus 001 Device 002: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg | grep usb

> [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.16.0-45-generic root=/dev/mapper/ubuntu--vg-root ro acpi=force irqpoll quiet splash usbcore.autosuspend=-1 vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-45-generic root=/dev/mapper/ubuntu--vg-root ro acpi=force irqpoll quiet splash usbcore.autosuspend=-1 vt.handoff=7
[    0.266637] usbcore: registered new interface driver usbfs
[    0.266656] usbcore: registered new interface driver hub
[    0.266690] usbcore: registered new device driver usb
[    1.172209] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.172212] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.172214] usb usb1: Product: xHCI Host Controller
[    1.172217] usb usb1: Manufacturer: Linux 3.16.0-45-generic xhci_hcd
[    1.172219] usb usb1: SerialNumber: 0000:00:14.0
[    1.175456] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.175459] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.175461] usb usb2: Product: xHCI Host Controller
[    1.175464] usb usb2: Manufacturer: Linux 3.16.0-45-generic xhci_hcd
[    1.175466] usb usb2: SerialNumber: 0000:00:14.0
[    1.176289] usb: failed to peer usb2-port4 and usb1-port3 by location (usb2-port4:none) (usb1-port3:usb2-port3)
[    1.176292] usb usb2-port4: failed to peer to usb1-port3 (-16)
[    1.176294] usb: port power management may be unreliable
[    1.486164] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.616825] usb 1-4: New USB device found, idVendor=0489, idProduct=e07a
[    1.616830] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.616833] usb 1-4: Product: BCM20702A0
[    1.616835] usb 1-4: Manufacturer: Broadcom Corp
[    1.616838] usb 1-4: SerialNumber: 38B1DBE4550C
[    1.782279] usb 1-7: new high-speed USB device number 3 using xhci_hcd
[    1.953482] usb 1-7: New USB device found, idVendor=5986, idProduct=0535
[    1.953487] usb 1-7: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.953490] usb 1-7: Product: Lenovo EasyCamera
[    1.953492] usb 1-7: Manufacturer: Generic
[    1.953494] usb 1-7: SerialNumber: 200901010001
[    2.070563] usb 1-8: new full-speed USB device number 4 using xhci_hcd
[    2.264888] usb 1-8: New USB device found, idVendor=048d, idProduct=8386
[    2.264893] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.264896] usb 1-8: Product: ITE Device(8386)
[    2.264898] usb 1-8: Manufacturer: ITE Tech. Inc.
[    2.306480] usbcore: registered new interface driver usbhid
[    2.306482] usbhid: USB HID core driver
[   14.604861] usbcore: registered new interface driver btusb
[   14.846723] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input15
[   14.846894] usbcore: registered new interface driver uvcvideo


This line makes me suscipious:

> failed to peer usb2-port4 and usb1-port3 by location (usb2-port4:none) (usb1-port3:usb2-port3)

---

