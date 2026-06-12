---
title: "Booting from USB"
date: 2011-10-23
forum: Hardware
---

### Post by shawnhcorey on 2011-10-23
I have an AMD64 motherboard with American Megatrends BIOS but I can't figure out how to get it to boot from USB. I have a USB stick properly configured with an Ubuntu ISO (at least, when I plug it in, it asks if I want to start the Update Manager, just like a CD) but when I go into the BIOS, I can't find out where to tell it to boot from USB.

How do I determine (from Ubuntu) which version of the BIOS I have?

Is there any way to change the configuration of the BIOS from Ubuntu?

---

### Post by diasf on 2011-10-23
In most modern bios, if you press F9 (instead of the bios key) it will show a menu for you to chose from where to boot. Sometimes is F12... point is, the function exists :)

---

### Post by shawnhcorey on 2011-10-23
Tried it but it didn't find any device on the USB port. :(

I'm not sure there BIOS can boot from USB. That's why I was wondering if there was a way to examine it from Ubuntu.

---

### Post by oldfred on 2011-10-23
How old is computer. It was about 5 years ago that BIOS were updated to include booting from USB ports even though USB ports had been around for years.

If a new system are you using a USB3 port, try a USB2 port.

---

### Post by shawnhcorey on 2011-10-23
The first entry in its tech journal is 2010.8.31. Its got 6 USB ports, two on the front and 4 on the motherboard (back). How do I determine if they're v2 or v3?

---

### Post by oldfred on 2011-10-23
Ports have different speeds. I would just try different ones.
This may tell something:
```
sudo lsusb
```


Workaround to get USB3 to boot
[http://ubuntuforums.org/showthread.php?t=1628665](http://ubuntuforums.org/showthread.php?t=1628665)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"

[http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2)
The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller
[http://en.wikipedia.org/wiki/USB3#USB_3.0](http://en.wikipedia.org/wiki/USB3#USB_3.0)
SuperSpeed (USB 3.0) rate of 4800 Mbit/s (~572 MB/s).
But speeds are more limited by devices at each end.

---

### Post by shawnhcorey on 2011-10-23
```
$ sudo lsusb
Bus 001 Device 007: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 003: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 001 Device 008: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
$ 

```
```
$ sudo lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/10p, 12M
    |__ Port 3: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 3: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
    |__ Port 4: Dev 3, If 0, Class=HID, Driver=usbhid, 1.5M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/10p, 480M
    |__ Port 5: Dev 8, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 6: Dev 7, If 0, Class=stor., Driver=usb-storage, 480M
$ 

```

Bus 01 is the front panel. Bus 02 is the motherboard. The rest I have no idea what they mean.

---

### Post by oldfred on 2011-10-23
It looks like Bus 01 front panel are the USB2 ports as they show 480M. I would be booting from those, but they should work without issue if flash drive is correctly configured.

This should create a text file with info on BIOS:
sudo dmidecode > bios.txt

This creates HTML file with lots of system info:
HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

---

### Post by Gawains Green Knight on 2011-10-23
I assume you can find a boot menu? If it doesn't show up then you might also want to try a different USB drive. I had a nightmare trying to install on my netbook, until I realized it was the drive I was using.... although the drive worked on other machines.

---

### Post by campbelt on 2011-10-23
Try holding down the esc key while booting.

---

### Post by Insomn1a on 2011-10-24
ive ran into the same issue before and unless it shows a USB or removable media as part of the boot priorities i dont believe that it will be possible, I would look in your BIOS and check out the boot priorities where you can select CD, hard drive, etc.   If you see removable media or USB listed in there you should be able to.

---

### Post by shawnhcorey on 2011-10-24
> **campbelt said:**
> Try holding down the esc key while booting.

Tried it. Ubuntu goes into an infinite loop of starting and stopping services.

---

