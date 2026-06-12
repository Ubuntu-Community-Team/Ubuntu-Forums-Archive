---
title: "Laptop does not recognize external usb hard disks, read/64 error -71"
date: 2022-12-03
forum: Hardware
---

### Post by Peter_Brandon on 2022-12-03
My laptop, which I bought 1.5 years ago and have hardly used, always had some problems recognizing one of my two external hard disks, but no problems with a second one.  With the problem disk, I had to repeatedly insert the disk, sometimes using a USB C hub, to get it to recognize.  

Recently, possibly after some updates, the laptop is utterly refusing to recognize either drive, including the one that had no problems before.  A much older desktop running exactly the same OS has no problems recognizing both external disks.  I use external disks to synchronize my computers, so the laptop is now largely useless to me, despite being in good shape otherwise.

When I plug in the 'good' hard disk to my laptop dmesg -w shows this:
```
[   99.788122] usb 1-2: new low-speed USB device number 5 using xhci_hcd
[   99.916161] usb 1-2: device descriptor read/64, error -71
[  100.152170] usb 1-2: device descriptor read/64, error -71
[  100.388130] usb 1-2: new low-speed USB device number 6 using xhci_hcd
[  100.516088] usb 1-2: device descriptor read/64, error -71
[  100.752170] usb 1-2: device descriptor read/64, error -71
[  100.860254] usb usb1-port2: attempt power cycle
[  101.272129] usb 1-2: new low-speed USB device number 7 using xhci_hcd
[  101.272689] usb 1-2: Device not responding to setup address.
[  101.480853] usb 1-2: Device not responding to setup address.
[  101.688133] usb 1-2: device not accepting address 7, error -71
[  101.816156] usb 1-2: new low-speed USB device number 8 using xhci_hcd
[  101.816704] usb 1-2: Device not responding to setup address.
[  102.024702] usb 1-2: Device not responding to setup address.
[  102.232127] usb 1-2: device not accepting address 8, error -71
[  102.232222] usb usb1-port2: unable to enumerate USB device
```

I've looked online for 'read/64, error -71' and have found instances of the problem being solved.  I've tried these solutions and they had no effect.  This includes 
[LIST=1]
[*]Adding a /etc/modprobe.d/options.conf file with the line:  options usbcore use_both_schemes=y .  Rebooting.  From [https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/](https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/) 
[*]Adding usbcore.autosuspend=-1 to grub; update-grub; reboot.  From:  [https://askubuntu.com/questions/1140925/how-can-i-disable-usb-autosuspend-on-ubuntu-18-04](https://askubuntu.com/questions/1140925/how-can-i-disable-usb-autosuspend-on-ubuntu-18-04) . 
[/LIST]

I've also tried updating my bios, which has proven not possible after days of work.  My laptop is a less expensive HP model, no longer has Windows installed, and does not appear to have any options at boot-up (bios / uefi) for firmware or bios updates (so there apparently is no way to activate a Windows-created USB BIOS flash rescue USB).  The BIOS update says it cannot be applied under dos (FreeDOS).  WindowsPE (Hiren's BootCD) seems to go through the motions, but the BIOS remains unchanged.  Because it's a laptop and has microcontrollers, FlashROM would likely brick the laptop.  I've considered or tried every solution here:  [https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux) .

I don't know what the source of the problem is.  Because it's a newer laptop and the hard disks are older USB 2 SATA drives, maybe that has something to do with the problem.

---

### Post by Peter_Brandon on 2022-12-03
Here's what I see from dmesg -w when I plug it in to my old desktop (running the same OS and updates as the laptop):

```
[51766.949829] usb 2-4: new low-speed USB device number 10 using xhci_hcd
[51767.077612] usb 2-4: device descriptor read/64, error -71
[51767.313620] usb 2-4: device descriptor read/64, error -71
[51767.553597] usb 2-4: new low-speed USB device number 11 using xhci_hcd
[51767.681614] usb 2-4: device descriptor read/64, error -71
[51767.917633] usb 2-4: device descriptor read/64, error -71
[51768.025659] usb usb2-port4: attempt power cycle
[51768.445583] usb 2-4: new high-speed USB device number 12 using xhci_hcd
[51768.471365] usb 2-4: New USB device found, idVendor=1058, idProduct=25a1, bcdDevice=10.13
[51768.471368] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[51768.471369] usb 2-4: Product: Elements 25A1
[51768.471371] usb 2-4: Manufacturer: Western Digital
[51768.471372] usb 2-4: SerialNumber: 575837314135374C44325646
[51768.472736] usb-storage 2-4:1.0: USB Mass Storage device detected
[51768.472836] scsi host7: usb-storage 2-4:1.0
[51769.498182] scsi 7:0:0:0: Direct-Access     WD       Elements 25A1    1013 PQ: 0 ANSI: 6
[51769.498429] sd 7:0:0:0: Attached scsi generic sg8 type 0
[51769.499619] sd 7:0:0:0: [sdh] Spinning up disk...
[51770.521582] .....ready
[51774.617886] sd 7:0:0:0: [sdh] 3906963456 512-byte logical blocks: (2.00 TB/1.82 TiB)
[51774.618238] sd 7:0:0:0: [sdh] Write Protect is off
[51774.618240] sd 7:0:0:0: [sdh] Mode Sense: 47 00 10 08
[51774.618615] sd 7:0:0:0: [sdh] No Caching mode page found
[51774.618618] sd 7:0:0:0: [sdh] Assuming drive cache: write through
[51774.840288]  sdh: sdh4
[51774.860151] sd 7:0:0:0: [sdh] Attached SCSI disk
[
```

So, comparing this to the same for the laptop, apparently the initial 'read/64, error -71' is not a problem.  The problem seems to be that the laptop continues to try to scan the drive in low speed, while the desktop switches to looking for a high speed device and recognizes exactly what kind of drive is attached and then connects to it.

I've also tried attaching the drive to another laptop bought at the same time as the laptop I want to fix (also running the same OS version), and it also is unable to read the usb drive.

I'm wondering if the laptops are missing some crucial software package that's needed to read the usb hard disk.  Or perhaps there is some configuration change I need to get the USB ports to look for high speed devices.

---

### Post by Peter_Brandon on 2022-12-03
I compared the output of the following command on both the laptop and the desktop:

lsmod | grep usb

The desktop has a number of likely relevant modules loaded that the laptop does not: usbhid, hid, usb_storage, scsi_mod .  

However, using dpkg -S, I see that all of the modules are currently present in the running kernel on the laptop.  Modules should normally load as needed by a usb device, thanks to udev .  What I'm unclear about is why the needed modules are not being called.  The desktop does have an internal scsi drive, so the OS could have been installed around that.

---

### Post by Peter_Brandon on 2022-12-13
Apparently the problem was due to insufficient power, at least in part.  I got a powered USB-C hub and can consistently recognize my external scsi drive--but only if the drive is propped up vertically on its short edge.  I have no clue why the position matters, beyond thinking that perhaps there is less friction in this position (not sure how).

---

