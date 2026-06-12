---
title: "USB Flash Memory Stick?"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by SeeleyUSMC on 2005-03-19
I can't seem to access my SanDisk Cruzer Mini 256 from Ubuntu.  I have tried starting up with it removed and then putting it in, and starting with it already in.  I looked in my device manager and it says it knows that something is plugged into the USB port, but it doesn't know what it does.  It knows the hardware info though...Windows can't use it either because I can't format it in Windows.  I would like to format it in Ubuntu, but can't figure out how to access it.

---

### Post by songochain on 2005-03-19
[QUOTE=SeeleyUSMC]I can't seem to access my SanDisk Cruzer Mini 256 from Ubuntu.  I have tried starting up with it removed and then putting it in, and starting with it already in.  I looked in my device manager and it says it knows that something is plugged into the USB port, but it doesn't know what it does.  It knows the hardware info though...Windows can't use it either because I can't format it in Windows.  I would like to format it in Ubuntu, but can't figure out how to access it.[/QUOTE]
 Try sudo mount -t vfat /dev/sda1 /mnt/usb, but if it hasnt a format try with sudo mount /dev/sda1 /mnt/usb
usb dir must be created

---

### Post by ac_dispatcher on 2005-03-20
I have a usb card reader

I plugged it in and checked my /var/log/syslog file

here it what came up:
```

Mar 20 11:39:04 localhost kernel: input: USB HID v1.00 Mouse [0461:4d09] on usb-0000:00:02.0-2
Mar 20 11:39:06 localhost usb.agent[32725]:      usb-storage: loaded successfully
Mar 20 11:39:11 localhost kernel: usb 2-1: new full speed USB device using ohci_hcd and address 3
Mar 20 11:39:11 localhost kernel: Initializing USB Mass Storage driver...
Mar 20 11:39:11 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Mar 20 11:39:11 localhost kernel: usbcore: registered new driver usb-storage
Mar 20 11:39:11 localhost kernel: USB Mass Storage support registered.
Mar 20 11:39:11 localhost kernel: usb-storage: device found at 3
Mar 20 11:39:11 localhost kernel: usb-storage: waiting for device to settle before scanning
Mar 20 11:39:11 localhost kernel:   Vendor: Lexar     Model: USB CF Reader     Rev: 0113
Mar 20 11:39:11 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar 20 11:39:11 localhost kernel: usb-storage: device scan complete
Mar 20 11:39:11 localhost scsi.agent[469]:      sd_mod: loaded sucessfully
Mar 20 11:39:11 localhost udev[507]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
Mar 20 11:39:11 localhost udev[507]: creating device node '/dev/sda'
Mar 20 11:39:11 localhost udev[527]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda1' becomes '%k'
Mar 20 11:39:11 localhost udev[527]: creating device node '/dev/sda1'

```

So I know its sda1

also I use KDE so I opened konqueror and typed:

media:///

plugged in my card reader and within a few seconds it showed up. ;-)

---

### Post by SeeleyUSMC on 2005-03-20
fdisk /dev/sda1 seemed to work.  I just didn't know where to look for the USB.  After formatting it to a FAT32, I was able to use it on bot Linux and Windows partitions.

---

### Post by gnutux on 2005-03-21
I have noticed that alot of SanDisk products don't work with Linux. I have a friend who tried to plug his SanDisk in his USB ports on his laptop and Linux can't detect it. It seems SanDisk USB discs aren't that universal afterall.

gnutux

---

### Post by Heli0s on 2005-03-21
I also have some problems with my USB Flash Disk.

If i plug it in dmesg come's up with:

```
usb 2-1: new full speed USB device using uhci_hcd and address 5
usb 2-1: device descriptor read/64, error -71
usb 2-1: device descriptor read/64, error -71
```

and I dont have a */var/sda1*. 

The disk is formated as fat.

any idea's?

P.S. the same flash disk worked "out of the box" on warty

---

