---
title: "USB 2.0 ports not working 14.04 device descriptor read/64, error -32"
date: 2015-05-05
forum: Hardware
---

### Post by alex305 on 2015-05-05
Hello I wonder if someone can help me with this. I have searched but yet to find an answer that works. 

Ubuntu 14.04 fresh install on a custom built PC using a Gigabyte 990XA-UD3 motherboard. The BIOS was updated to the latest version using Q-flash and I chose to load the defaults (where it said everything would work). 

USB 3.0 ports work, USB 2.0 ports do not and there are 8 xUSD 2.0 ports and 3x USB 3.0 ports. 
Physically for example I plug in the USB mouse I am using into a USB 2.0 port, the laser light flashes, then goes off. 
The mouse fails to work, as does any other USB device plugged into the USB 2.0 ports. 

lsusb brings 
```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 006: ID 192f:0916 Avago Technologies, Pte. 
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 008 Device 002: ID 1a2c:0e24 China Resource Semico Co., Ltd 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

when I run dmesg I see (at the end) 

```
[ 1867.756542] usb 5-2: new low-speed USB device number 24 using ohci-pci
[ 1868.164189] usb 5-2: device not accepting address 24, error -32
[ 1868.300101] usb 5-2: new low-speed USB device number 25 using ohci-pci
[ 1868.707749] usb 5-2: device not accepting address 25, error -32
[ 1868.843660] usb 5-2: new low-speed USB device number 26 using ohci-pci
[ 1868.983546] usb 5-2: device descriptor read/64, error -32
[ 1869.634998] usb 5-2: device not accepting address 26, error -32
[ 1869.770899] usb 5-2: new low-speed USB device number 27 using ohci-pci
[ 1870.314436] usb 5-2: device not accepting address 27, error -32
[ 1870.314474] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 1876.705297] usb 10-1: new low-speed USB device number 6 using xhci_hcd
[ 1876.749312] usb 10-1: New USB device found, idVendor=192f, idProduct=0916
[ 1876.749320] usb 10-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 1876.749325] usb 10-1: Product: USB Optical Mouse
[ 1876.749571] usb 10-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 1876.763922] input: USB Optical Mouse as /devices/pci0000:00/0000:00:0a.0/0000:04:00.0/usb10/10-1/10-1:1.0/input/input21
[ 1876.764180] hid-generic 0003:192F:0916.0006: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:04:00.0-1/input0
```

When done, the only things plugged into the USB 3.0 ports are the keyboard and mouse.

I've tried fixes suggested from [http://ubuntuforums.org/showthread.php?t=2191520&page=2](http://ubuntuforums.org/showthread.php?t=2191520&page=2) this thread and others but most threads remain unsolved or ignored, I've yet to see what will work. 

Grateful for any help or suggestions.

Cheers

---

### Post by alex305 on 2015-05-06
Bump. Anyone?

---

### Post by alex305 on 2015-05-18
For the benefit of anyone else who had this issue I finally solved it. However *grumble* at the lack of support. 
It turns out the issue is to do with the Gigabyte mother board. I noticed that all USBs worked in BIOS but not when ubuntu was loaded. 
There is an option in BIOS / Peripherals to Enable IOMMU. No idea what's its for, but enabling this has made things work. Thank f*ck. This PC was beginning to look like an expensive doorstop. 
Kudos to the authors of: 

[http://unix.stackexchange.com/questions/72625/why-is-usb-not-working-in-linux-when-it-works-in-uefi-bios](http://unix.stackexchange.com/questions/72625/why-is-usb-not-working-in-linux-when-it-works-in-uefi-bios)
[http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055)

---

### Post by dino99 on 2015-05-18
IOMMU is a system specific IO mapping mechanism and can be used with most devices.

IOMMU sounds like a generic name for Intel VT-d and AMD IOV.

[https://en.wikipedia.org/wiki/IOMMU](https://en.wikipedia.org/wiki/IOMMU)

---

### Post by dino99 on 2015-05-18
IOMMU is a system specific IO mapping mechanism and can be used with most devices.

IOMMU sounds like a generic name for Intel VT-d and AMD IOV.

---

