---
title: "Behringer UCA222 Doesn't Show Up In Sound Preferences"
date: 2012-04-23
forum: Hardware
---

### Post by iTails on 2012-04-23
As I was rummaging through some stuff, I found my UCA222. I figured I could use it since my laptop onboard audio quality is pretty bad. My only problem is that it won't use this device. It shows up in Sound prefs but doesn't play through the external sound.

Here is my output from LSUSB.

```
robert@robert-ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 174f:1120 Syntek 
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 003 Device 003: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
robert@robert-ubuntu:~$ 

```

It shows PCM2902 as the same thing in sound prefs as well.

Here is dmesg output

```
[ 1220.985881] usb 3-4: USB disconnect, device number 3
[ 1223.880087] usb 3-4: new full speed USB device number 4 using ohci_hcd
[ 1224.192192] input: Burr-Brown from TI               USB Audio CODEC  as /devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4:1.3/input/input18
[ 1224.192388] generic-usb 0003:08BB:2902.0004: input,hidraw2: USB HID v1.00 Device [Burr-Brown from TI               USB Audio CODEC ] on usb-0000:00:04.0-4/input3

```

---

