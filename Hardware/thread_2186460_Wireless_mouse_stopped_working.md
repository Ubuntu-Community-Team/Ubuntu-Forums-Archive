---
title: "Wireless mouse stopped working"
date: 2013-11-07
forum: Hardware
---

### Post by rolltide101x on 2013-11-07
My USB wireless mouse has been working for months and for some reason last night it just stopped working. (I am on Ubuntu 13.10)

it is a usb dongle that I plug into a usb port and then the mouse automatically syncs to it. 

```
celina@celina-Satellite-L755:~$ lsusb
Bus 002 Device 006: ID 1d57:0016 Xenta 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b28e Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```




```
celina@celina-Satellite-L755:~$ dmesg | grep -i usb
[    0.238682] ACPI: bus type USB registered
[    0.238700] usbcore: registered new interface driver usbfs
[    0.238710] usbcore: registered new interface driver hub
[    0.238739] usbcore: registered new device driver usb
[    0.644688] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.644816] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.660367] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.660390] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.660392] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.660394] usb usb1: Product: EHCI Host Controller
[    0.660396] usb usb1: Manufacturer: Linux 3.11.0-031100-generic ehci_hcd
[    0.660398] usb usb1: SerialNumber: 0000:00:1a.0
[    0.660496] hub 1-0:1.0: USB hub found
[    0.660680] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.676376] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.676392] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.676395] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.676397] usb usb2: Product: EHCI Host Controller
[    0.676398] usb usb2: Manufacturer: Linux 3.11.0-031100-generic ehci_hcd
[    0.676400] usb usb2: SerialNumber: 0000:00:1d.0
[    0.676485] hub 2-0:1.0: USB hub found
[    0.676571] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.676578] uhci_hcd: USB Universal Host Controller Interface driver
[    0.972620] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.105056] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.105061] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.105353] hub 1-1:1.0: USB hub found
[    1.216726] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.349198] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.349207] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.349626] hub 2-1:1.0: USB hub found
[    1.421052] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    1.516449] usb 1-1.1: New USB device found, idVendor=1d57, idProduct=0016
[    1.516459] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.516464] usb 1-1.1: Product: HID Wireless Mouse
[    1.516469] usb 1-1.1: Manufacturer: HID Wireless Mouse
[    1.526186] usbcore: registered new interface driver usbhid
[    1.526193] usbhid: USB HID core driver
[    1.528117] input: HID Wireless Mouse HID Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input4
[    1.528281] hid-generic 0003:1D57:0016.0001: input,hidraw0: USB HID v1.10 Mouse [HID Wireless Mouse HID Wireless Mouse] on usb-0000:00:1a.0-1.1/input0
[    1.589158] usb 1-1.4: new high-speed USB device number 4 using ehci-pci
[    1.710847] usb 1-1.4: New USB device found, idVendor=04f2, idProduct=b28e
[    1.710856] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.710861] usb 1-1.4: Product: TOSHIBA Web Camera
[    1.710865] usb 1-1.4: Manufacturer: Sonix Technology Co., Ltd.
[   11.550000] input: TOSHIBA Web Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input11
[   11.550143] usbcore: registered new interface driver uvcvideo
[   11.550146] USB Video Class driver (1.1.1)
[   73.650335] usb 1-1.1: USB disconnect, device number 3
[   79.396982] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[   79.492521] usb 2-1.2: New USB device found, idVendor=1d57, idProduct=0016
[   79.492528] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   79.492532] usb 2-1.2: Product: HID Wireless Mouse
[   79.492535] usb 2-1.2: Manufacturer: HID Wireless Mouse
[   79.494359] input: HID Wireless Mouse HID Wireless Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input12
[   79.494586] hid-generic 0003:1D57:0016.0002: input,hidraw0: USB HID v1.10 Mouse [HID Wireless Mouse HID Wireless Mouse] on usb-0000:00:1d.0-1.2/input0
[  433.117624] usb 2-1.2: USB disconnect, device number 3
[  433.717944] usb 2-1.2: new full-speed USB device number 4 using ehci-pci
[  433.813396] usb 2-1.2: New USB device found, idVendor=1d57, idProduct=0016
[  433.813409] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  433.813423] usb 2-1.2: Product: HID Wireless Mouse
[  433.813426] usb 2-1.2: Manufacturer: HID Wireless Mouse
[  433.815069] input: HID Wireless Mouse HID Wireless Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13
[  433.815320] hid-generic 0003:1D57:0016.0003: input,hidraw0: USB HID v1.10 Mouse [HID Wireless Mouse HID Wireless Mouse] on usb-0000:00:1d.0-1.2/input0
[  474.826633] usb 2-1.2: USB disconnect, device number 4
[  475.728432] usb 2-1.2: new full-speed USB device number 5 using ehci-pci
[  475.823235] usb 2-1.2: New USB device found, idVendor=1d57, idProduct=0016
[  475.823239] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  475.823242] usb 2-1.2: Product: HID Wireless Mouse
[  475.823244] usb 2-1.2: Manufacturer: HID Wireless Mouse
[  475.824600] input: HID Wireless Mouse HID Wireless Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input14
[  475.824782] hid-generic 0003:1D57:0016.0004: input,hidraw0: USB HID v1.10 Mouse [HID Wireless Mouse HID Wireless Mouse] on usb-0000:00:1d.0-1.2/input0
[  536.303760] usb 2-1.2: USB disconnect, device number 5
[  538.604251] usb 2-1.2: new full-speed USB device number 6 using ehci-pci
[  538.700103] usb 2-1.2: New USB device found, idVendor=1d57, idProduct=0016
[  538.700115] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  538.700120] usb 2-1.2: Product: HID Wireless Mouse
[  538.700125] usb 2-1.2: Manufacturer: HID Wireless Mouse
[  538.701826] input: HID Wireless Mouse HID Wireless Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input15
[  538.702106] hid-generic 0003:1D57:0016.0005: input,hidraw0: USB HID v1.10 Mouse [HID Wireless Mouse HID Wireless Mouse] on usb-0000:00:1d.0-1.2/input0
celina@celina-Satellite-L755:~$ 

```

If you need anything else let me know. I tried different USB Ports and taking the battery out of the mouse neither worked. I am about to test if the mouse is working in Windows 8. I will report back. Thanks for any help.

---

