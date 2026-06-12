---
title: "Gembird USB headset &quot;unable to enumerate USB device on port&quot;"
date: 2011-03-01
forum: Hardware
---

### Post by Freaky#Funga on 2011-03-01
Hi there,
I was searching this forum and also mr. Google, but with no luck.
When I plug my gembird usb headset, I got this output from dmesg:
```
[18681.256094] usb 3-2: new full speed USB device using uhci_hcd and address 17
[18681.376105] usb 3-2: device descriptor read/64, error -71
[18681.600068] usb 3-2: device descriptor read/64, error -71
[18681.816999] usb 3-2: new full speed USB device using uhci_hcd and address 18
[18681.940066] usb 3-2: device descriptor read/64, error -71
[18682.165078] usb 3-2: device descriptor read/64, error -71
[18682.380097] usb 3-2: new full speed USB device using uhci_hcd and address 19
[18682.788056] usb 3-2: device not accepting address 19, error -71
[18682.904083] usb 3-2: new full speed USB device using uhci_hcd and address 20
[18683.312047] usb 3-2: device not accepting address 20, error -71
[18683.312134] hub 3-0:1.0: unable to enumerate USB device on port 2
```
Tried some workarounds:
```
# echo -1 > /sys/module/usbcore/parameters/autosuspend
# echo Y > /sys/module/usbcore/parameters/old_scheme_first
```
with no luck.
Here is output of some commands which may be helpful for someone who could know where is the problem:
```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


# uname -a
Linux TuxNtb 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux


# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 0b38:0003  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 028: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
note: lsusb output is exactly the same before and after connecting USB headset.

Thanks in advance :)

---

