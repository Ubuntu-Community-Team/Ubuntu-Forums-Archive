---
title: "Ubuntu 16.04 LTS Desktop USB 3.0 Ports Not Working, Error -110"
date: 2016-06-25
forum: Hardware
---

### Post by Rocklobstar on 2016-06-25
Hello,

I am having an USB issue with my recent install dual boot next to windows 10 of Ubuntu 16.04 LTS.

To give landscape, I have 4 USB ports on the front of my tower (2 USB 3.0 and 2 USB 2.0).  I have 2 USB 2.0 on the back and 4 USB 3.0 on the back.

The issue is that my USB 3.0 no longer work on the back.  Every other USB port works (3.0 works on the front).

I also have the issue of the back USB 3.0 group not working if I reboot into windows.  I get error 43.  If I shut down and unplug power to the computer, completely shutting off power to the mother board, and then turn it back on, it will work again.

I have searched all I could, but cannot seem to find any answers as to why this may be happening.  

Best I could figure out is that some of the ports are getting -110 errors.


please let me know if I need to give more information.  I would like to  figure this out so I can smoothly transition from Windows to Ubuntu.

Thank you so much for your help in advance.

Here are the outputs to the commands for some more information:

```
 sudo dmesg | grep -i usb 
```

```
[    0.182351] ACPI: bus type USB registered
[    0.182360] usbcore: registered new interface driver usbfs
[    0.182365] usbcore: registered new interface driver hub
[    0.182378] usbcore: registered new device driver usb
[    0.621472] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.621548] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.638830] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.638853] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.638854] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.638855] usb usb1: Product: EHCI Host Controller
[    0.638856] usb usb1: Manufacturer: Linux 4.4.0-24-generic ehci_hcd
[    0.638856] usb usb1: SerialNumber: 0000:00:1a.0
[    0.638923] hub 1-0:1.0: USB hub found
[    0.639064] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.654834] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.654850] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.654851] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.654851] usb usb2: Product: EHCI Host Controller
[    0.654852] usb usb2: Manufacturer: Linux 4.4.0-24-generic ehci_hcd
[    0.654853] usb usb2: SerialNumber: 0000:00:1d.0
[    0.654916] hub 2-0:1.0: USB hub found
[    0.654996] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.655012] uhci_hcd: USB Universal Host Controller Interface driver
[    0.655080] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.656203] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.656204] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.656205] usb usb3: Product: xHCI Host Controller
[    0.656206] usb usb3: Manufacturer: Linux 4.4.0-24-generic xhci-hcd
[    0.656207] usb usb3: SerialNumber: 0000:00:14.0
[    0.656268] hub 3-0:1.0: USB hub found
[    0.657800] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.657823] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.657824] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.657825] usb usb4: Product: xHCI Host Controller
[    0.657825] usb usb4: Manufacturer: Linux 4.4.0-24-generic xhci-hcd
[    0.657826] usb usb4: SerialNumber: 0000:00:14.0
[    0.657886] hub 4-0:1.0: USB hub found
[    0.950863] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.970844] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    0.970851] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.083161] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.083172] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.083444] hub 1-1:1.0: USB hub found
[    1.107307] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.107309] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.107576] hub 2-1:1.0: USB hub found
[    6.190949] usb 4-3: new SuperSpeed USB device number 2 using xhci_hcd
[    6.208899] usb 4-3: New USB device found, idVendor=174c, idProduct=3074
[    6.208901] usb 4-3: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    6.208902] usb 4-3: Product: AS2107
[    6.208914] usb 4-3: Manufacturer: ASMedia
[    6.208915] usb 4-3: SerialNumber: USB2.0 Hub
[   11.207004] usb 4-3: Enable of device-initiated U2 failed.
[   11.207866] hub 4-3:1.0: USB hub found
[   11.211043] usb 3-3: device descriptor read/all, error -110
[   11.322918] usb 3-3: new high-speed USB device number 3 using xhci_hcd
[   16.207049] usb 4-3: Enable of device-initiated U1 failed.
[   21.451087] usb 3-3: device descriptor read/all, error -110
[   21.562993] usb 3-3: new high-speed USB device number 4 using xhci_hcd
[   26.579076] usb 3-3: device descriptor read/8, error -110
[   31.699143] usb 3-3: device descriptor read/8, error -110
[   31.915065] usb 3-3: new high-speed USB device number 5 using xhci_hcd
[   36.931188] usb 3-3: device descriptor read/8, error -110
[   42.051183] usb 3-3: device descriptor read/8, error -110
[   42.155133] usb usb3-port3: unable to enumerate USB device
[   42.395125] usb 3-6: new full-speed USB device number 6 using xhci_hcd
[   42.525539] usb 3-6: New USB device found, idVendor=05e3, idProduct=0604
[   42.525541] usb 3-6: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   42.525551] usb 3-6: Product: USB Hub
[   42.525619] usb 3-6: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[   42.526217] hub 3-6:1.0: USB hub found
[   42.767140] usb 3-14: new full-speed USB device number 7 using xhci_hcd
[   43.551271] usb 3-14: New USB device found, idVendor=046d, idProduct=0a1f
[   43.551272] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   43.551283] usb 3-14: Product: Logitech G930 Headset
[   43.551284] usb 3-14: Manufacturer: Logitech
[   43.551416] usb 3-14: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[   43.564104] usbcore: registered new interface driver usbhid
[   43.564105] usbhid: USB HID core driver
[   43.567460] input: Logitech Logitech G930 Headset as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.3/0003:046D:0A1F.0001/input/input14
[   43.576298] usbcore: registered new interface driver snd-usb-audio
[   43.623148] usb 3-6.3: new full-speed USB device number 8 using xhci_hcd
[   43.623468] hid-generic 0003:046D:0A1F.0001: input,hiddev0,hidraw0: USB HID v1.01 Device [Logitech Logitech G930 Headset] on usb-0000:00:14.0-14/input3
[   43.712770] usb 3-6.3: New USB device found, idVendor=1532, idProduct=0036
[   43.712771] usb 3-6.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   43.712772] usb 3-6.3: Product: Razer Naga Hex
[   43.712773] usb 3-6.3: Manufacturer: Razer
[   43.714080] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6.3/3-6.3:1.0/0003:1532:0036.0002/input/input15
[   43.714317] hid-generic 0003:1532:0036.0002: input,hidraw1: USB HID v1.11 Mouse [Razer Razer Naga Hex] on usb-0000:00:14.0-6.3/input0
[   43.715277] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6.3/3-6.3:1.1/0003:1532:0036.0003/input/input16
[   43.823320] hid-generic 0003:1532:0036.0003: input,hidraw2: USB HID v1.11 Keyboard [Razer Razer Naga Hex] on usb-0000:00:14.0-6.3/input1
[   43.895150] usb 3-6.4: new full-speed USB device number 9 using xhci_hcd
[   43.986059] usb 3-6.4: New USB device found, idVendor=1532, idProduct=0102
[   43.986061] usb 3-6.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   43.986062] usb 3-6.4: Product: Razer Tarantula Keyboard
[   43.986062] usb 3-6.4: Manufacturer: Razer
[   43.986174] usb 3-6.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   43.986176] usb 3-6.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[   43.987654] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6.4/3-6.4:1.0/0003:1532:0102.0004/input/input17
[   44.043349] hid-generic 0003:1532:0102.0004: input,hidraw3: USB HID v1.00 Keyboard [Razer Razer Tarantula Keyboard] on usb-0000:00:14.0-6.4/input0
[   44.044829] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6.4/3-6.4:1.1/0003:1532:0102.0005/input/input18
[   44.099331] hid-generic 0003:1532:0102.0005: input,hidraw4: USB HID v1.00 Device [Razer Razer Tarantula Keyboard] on usb-0000:00:14.0-6.4/input1
[   47.082340] usb 3-6: USB disconnect, device number 6
[   47.082342] usb 3-6.3: USB disconnect, device number 8
[   47.155202] usb 3-6.4: USB disconnect, device number 9
[   53.488293] usb 3-14: USB disconnect, device number 7
[   70.406895] usb 3-3: new high-speed USB device number 10 using xhci_hcd
[   80.534476] usb 3-3: device descriptor read/all, error -110
[   80.646435] usb 3-3: new high-speed USB device number 11 using xhci_hcd
[   90.774262] usb 3-3: device descriptor read/all, error -110
[   90.886239] usb 3-3: new high-speed USB device number 12 using xhci_hcd
[   95.902226] usb 3-3: device descriptor read/8, error -110
[  101.022192] usb 3-3: device descriptor read/8, error -110
[  101.238165] usb 3-3: new high-speed USB device number 13 using xhci_hcd
[  106.254186] usb 3-3: device descriptor read/8, error -110
[  111.374179] usb 3-3: device descriptor read/8, error -110
[  111.478181] usb usb3-port3: unable to enumerate USB device
[  114.234182] usb 3-3: new high-speed USB device number 14 using xhci_hcd
[  124.362241] usb 3-3: device descriptor read/all, error -110
[  124.474227] usb 3-3: new high-speed USB device number 15 using xhci_hcd
[  134.601574] usb 3-3: device descriptor read/all, error -110
[  134.713543] usb 3-3: new high-speed USB device number 16 using xhci_hcd
[  139.728985] usb 3-3: device descriptor read/8, error -110
[  144.848459] usb 3-3: device descriptor read/8, error -110
[  145.064431] usb 3-3: new high-speed USB device number 17 using xhci_hcd
[  150.080004] usb 3-3: device descriptor read/8, error -110
[  155.199609] usb 3-3: device descriptor read/8, error -110
[  155.303606] usb usb3-port3: unable to enumerate USB device
[  155.799540] usb 3-14: new full-speed USB device number 18 using xhci_hcd
[  155.929981] usb 3-14: New USB device found, idVendor=05e3, idProduct=0604
[  155.929987] usb 3-14: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[  155.929990] usb 3-14: Product: USB Hub
[  155.930275] usb 3-14: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[  155.930902] hub 3-14:1.0: USB hub found
[  156.203476] usb 3-14.3: new full-speed USB device number 19 using xhci_hcd
[  156.293009] usb 3-14.3: New USB device found, idVendor=1532, idProduct=0036
[  156.293011] usb 3-14.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  156.293012] usb 3-14.3: Product: Razer Naga Hex
[  156.293013] usb 3-14.3: Manufacturer: Razer
[  156.294269] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.3/3-14.3:1.0/0003:1532:0036.0006/input/input19
[  156.294507] hid-generic 0003:1532:0036.0006: input,hidraw0: USB HID v1.11 Mouse [Razer Razer Naga Hex] on usb-0000:00:14.0-14.3/input0
[  156.295451] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.3/3-14.3:1.1/0003:1532:0036.0007/input/input20
[  156.403672] hid-generic 0003:1532:0036.0007: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer Naga Hex] on usb-0000:00:14.0-14.3/input1
[  156.475454] usb 3-14.4: new full-speed USB device number 20 using xhci_hcd
[  156.566353] usb 3-14.4: New USB device found, idVendor=1532, idProduct=0102
[  156.566354] usb 3-14.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  156.566356] usb 3-14.4: Product: Razer Tarantula Keyboard
[  156.566356] usb 3-14.4: Manufacturer: Razer
[  156.566474] usb 3-14.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  156.566477] usb 3-14.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[  156.567872] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.4/3-14.4:1.0/0003:1532:0102.0008/input/input21
[  156.623702] hid-generic 0003:1532:0102.0008: input,hidraw2: USB HID v1.00 Keyboard [Razer Razer Tarantula Keyboard] on usb-0000:00:14.0-14.4/input0
[  156.625274] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.4/3-14.4:1.1/0003:1532:0102.0009/input/input22
[  156.679669] hid-generic 0003:1532:0102.0009: input,hidraw3: USB HID v1.00 Device [Razer Razer Tarantula Keyboard] on usb-0000:00:14.0-14.4/input1
[ 1136.507972] usb 3-14.3: USB disconnect, device number 19
[ 1145.447912] usb 3-10: new full-speed USB device number 21 using xhci_hcd
[ 1145.577798] usb 3-10: New USB device found, idVendor=1532, idProduct=0036
[ 1145.577805] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1145.577809] usb 3-10: Product: Razer Naga Hex
[ 1145.577813] usb 3-10: Manufacturer: Razer
[ 1145.580003] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/0003:1532:0036.000A/input/input23
[ 1145.636207] hid-generic 0003:1532:0036.000A: input,hidraw0: USB HID v1.11 Mouse [Razer Razer Naga Hex] on usb-0000:00:14.0-10/input0
[ 1145.637600] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.1/0003:1532:0036.000B/input/input24
[ 1145.692037] hid-generic 0003:1532:0036.000B: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer Naga Hex] on usb-0000:00:14.0-10/input1
[ 1163.894487] usb 3-10: USB disconnect, device number 21
[ 1248.283314] usb 3-9: new full-speed USB device number 22 using xhci_hcd
[ 1248.413132] usb 3-9: New USB device found, idVendor=1532, idProduct=0036
[ 1248.413138] usb 3-9: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1248.413142] usb 3-9: Product: Razer Naga Hex
[ 1248.413144] usb 3-9: Manufacturer: Razer
[ 1248.415044] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.0/0003:1532:0036.000C/input/input25
[ 1248.415352] hid-generic 0003:1532:0036.000C: input,hidraw0: USB HID v1.11 Mouse [Razer Razer Naga Hex] on usb-0000:00:14.0-9/input0
[ 1248.416830] input: Razer Razer Naga Hex as /devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.1/0003:1532:0036.000D/input/input26
[ 1248.523375] hid-generic 0003:1532:0036.000D: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer Naga Hex] on usb-0000:00:14.0-9/input1
```

```
sudo lsusb
```
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 020: ID 1532:0102 Razer USA, Ltd Tarantula Keyboard
Bus 003 Device 023: ID 1532:0036 Razer USA, Ltd RZ01-0075, Gaming Mouse [Naga Hex]
Bus 003 Device 018: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

```
sudo lsusb -t
```
```
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
    |__ Port 3: Dev 2, If 0, Class=Hub, Driver=hub/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 14: Dev 18, If 0, Class=Hub, Driver=hub/4p, 12M
        |__ Port 3: Dev 23, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 3: Dev 23, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 4: Dev 20, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 4: Dev 20, If 1, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M


```

---

### Post by weatherman2 on 2016-06-25
Do you mean that the two USB 3.0 ports NEVER work in Ubuntu and if you reboot into Windows they also don't work - but once you power off completely then reboot into Windows, those two ports work perfectly in Windows until you boot back into Ubuntu?  Do they ever fail when you are in Windows when you haven't booted Ubuntu?

---

### Post by Rocklobstar on 2016-06-25
> [COLOR=#000000]Do you mean that the two USB 3.0 ports NEVER work in Ubuntu and if you reboot into Windows they also don't work - but once you power off completely then reboot into Windows, those two ports work perfectly in Windows until you boot back into Ubuntu? Do they ever fail when you are in Windows when you haven't booted Ubuntu?[/COLOR]

The two USB 3.0 ports on the front work correctly all the time.  It is the group of four USB 3.0 ports on the back of the tower.  But what you described is correct just exchange the 'two' with a 'four'.  They NEVER work in Ubuntu and rebooting into Windows they still do not work.  They will only work if I power down and unplug, cutting the power completely to the motherboard.

---

### Post by weatherman2 on 2016-06-25
What I am trying to understand is whether Ubuntu is causing the problem with your rear USB 3.0 ports or whether you have a hardware issue unrelated to the OS.

Again: if after you power down / unplug and boot into Windows, will your rear USB 3.0 ports continue to work again until you boot back into Ubuntu?  Or will they also fail in Windows again, even if you never boot Ubuntu?

---

### Post by Rocklobstar on 2016-06-25
> **weatherman2 said:**
> What I am trying to understand is whether Ubuntu is causing the problem with your rear USB 3.0 ports or whether you have a hardware issue unrelated to the OS.

Again: if after you power down / unplug and boot into Windows, will your rear USB 3.0 ports continue to work again until you boot back into Ubuntu?  Or will they also fail in Windows again, even if you never boot Ubuntu?


They will continue to work no problem until i boot back into Ubuntu.  Booting into Ubuntu causes them to fail.  Sorry, I hope this answer clears it up.

---

### Post by weatherman2 on 2016-06-25
If this isn't a fairly new PC, try booting an older version of Ubuntu like 14.04 LTS live from USB and see if you have the same issue.  Could be an incompatibility with the kernel you are using.

Check the motherboard manufacturer's website and see if they offer a newer BIOS version for your motherboard; if so, I'd upgrade (using Windows of course).

---

### Post by Rocklobstar on 2016-06-25
Thanks, I will look into that and give it a try.

It is about 3 years old.  Checking for a newer version of the BIOS to possibly fix a kernel issue could be the key.

---

### Post by cathect2 on 2016-06-30
I also have an Asmedia hub in my machine. And it has caused no end of headaches.

---

