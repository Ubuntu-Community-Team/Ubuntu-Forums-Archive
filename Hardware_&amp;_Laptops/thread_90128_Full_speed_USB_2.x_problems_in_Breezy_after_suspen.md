---
title: "Full speed USB 2.x problems in Breezy after suspend"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by coaxx on 2005-11-14
Hi,

having upgraded my fine working Hoary system to breezy I have a problem with my BENQ DVD DD EW162I connected to USB 2 on my Toshiba Satellite 5200-80. 

Everything seems to work fine before I use any suspend mode for the first time after booting. (Suspending S3 has worked very well with Hoary, so there shouldt be no reason not to use it or set acpi=off or something like that)

Here are my logs unplugging and plugging in my EW162I DVD-r/w **before** I have used any suspend mode (looks fine here..):

```


**plug off:**
usb 4-1: USB disconnect, address 5

**plug in:**
usb 4-1: new high speed USB device using ehci_hcd and address 6
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
usb-storage: already loaded
  Vendor: BENQ      Model: DVD DD EW162I     Rev: 47L9
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi2, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi2, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
sr_mod: loaded sucessfully (for cdrom)
sg: loaded sucessfully (for cdrom)

```

Ok after this lets try to test it **after** going to sleep:
```

sudo /etc/acpi/sleep.sh

```

OK coming back from S3 we listen to our logs:
```

usb 4-1: new high speed USB device using ehci_hcd and address 8
usb 4-1: device not accepting address 8, error -110
new high speed USB device using ehci_hcd and address 9
usb 4-1: device not accepting address 9, error -110
new high speed USB device using ehci_hcd and address 10
device not accepting address 10, error -110
new high speed USB device using ehci_hcd and address 11
device not accepting address 11, error -110

```

The same output will be generated for my Canon Scanner (USB 2.x). My Logitech Keyboard and mouse work well even after suspend, the are USB 1.1.
So my full speed USB (USB 2.x) DVD/CD writer and scanner (Canon N650U) are not working after suspend mode.

OK looking at these thread I found something about the same problem:
[http://www.ubuntuforums.org/showthread.php?t=89266](http://www.ubuntuforums.org/showthread.php?t=89266)

Unfortunatly the only hint there is to try a 

```

sudo modprobe -r ehci_hcd

```

Having done this, there seems to be an effect looking at the logs:

```

ehci_hcd 0000:02:06.2: remove, state 1
usb usb4: USB disconnect, address 1
ehci_hcd 0000:02:06.2: USB bus 4 deregistered
ACPI: PCI interrupt for device 0000:02:06.2 disabled

usb 2-1: new full speed USB device using ohci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb-storage: already loaded
   Vendor: BENQ      Model: DVD DD EW162I     Rev: 47L9
   Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi3, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi3, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
sr_mod: loaded sucessfully (for cdrom)
sg: loaded sucessfully (for cdrom)

```

Comparing this output to my first log-print when my DVD-RW was beeing connected before suspend-mode there seems to be no relevant difference.

Nevertheless the drive does not work now. Inserting a Data Cd will couse no action. K3b does not find the device. 
After another reinserting of the USB device automount will work and reading from a Data CD works also, but no way with K3b: it stops at "Scanning for cd devices.." on the splash screen. (Same results for my scanner, xsane will not finde any devices)

The only way to use DVD/CD writer and scanner is to do a complete reboot. So everytime my notebook has had a suspend mode I cannot write cds or use my scanner via full speed USB (USB 2.x).

Also unloading any USB related module (even all of them) before suspend-mode (using the MODULES option in /etc/default/acpi-support) will not solve the problem :( 

Anybody with more knowledge with this who can help me out here? Thank very much.

---

### Post by coaxx on 2005-11-15
[QUOTE=coaxx]
```

usb 4-1: new high speed USB device using ehci_hcd and address 8
**usb 4-1: device not accepting address 8, error -110**
new high speed USB device using ehci_hcd and address 9
**usb 4-1: device not accepting address 9, error -110**
new high speed USB device using ehci_hcd and address 10
**device not accepting address 10, error -110**
new high speed USB device using ehci_hcd and address 11
**device not accepting address 11, error -110**

```
[/QUOTE]

Really nobody can help me out here? My hole ubuntu installation on my Laptop is totaly useless if usb devices dont run proberly. I really hope to find someone who can help on this matter. :???:

---

