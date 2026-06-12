---
title: "Default response to USB flash drive"
date: 2009-06-01
forum: Hardware
---

### Post by lparsons42 on 2009-06-01
Is there a way to change the default response to inserting a USB flash drive?  I would like to setup my Kubuntu workstation to run a specific script from my home directory any time I insert a flash drive.  Is there a way to do this?

My aim with this is to setup my system to automatically backup the contents of the flash drive to my hard drive, so that if I lose the flash drive (needless to say this has happened more than once) I will still have a copy of its contents somewhere that was automatically copied over when I inserted said drive.

---

### Post by MichaelSammels on 2009-06-01
Normally when you insert a dialog box pops up asking you what you want to do, and you can set what you want it to do. However, what you want is more complex? Perhaps you could write a shell script? However this would need to be run manually.

---

### Post by lparsons42 on 2009-06-01
> **MichaelSammels said:**
> Normally when you insert a dialog box pops up asking you what you want to do, and you can set what you want it to do. However, what you want is more complex? Perhaps you could write a shell script? However this would need to be run manually.

A shell script is exactly what I want to do; but I want the shell script to run automatically any time I insert a flash drive.

---

### Post by MichaelSammels on 2009-06-01
Try this:

[http://ubuntuforums.org/archive/index.php/t-239830.html](http://ubuntuforums.org/archive/index.php/t-239830.html)

---

### Post by lparsons42 on 2009-06-01
That is a good idea, unfortunately the > From the "K" Menu, one goes to System Settings > Peripherals > Storage Media
Doesn't exist anymore (Kubuntu 9.04).  I suspect I'll have to buy a new flash drive (since my current one is MIA), and then watch the logs to see what is invoked by Ubuntu when I insert it in order to figure out how to hack this together.

---

### Post by lparsons42 on 2009-06-01
Here is the response I see in dmesg when I plug in my usb flash drive:
```

[1044193.121862] usb 3-1.1: new full speed USB device using uhci_hcd and address 6
[1044193.225844] usb 3-1.1: not running at top speed; connect to a high speed hub
[1044193.258102] usb 3-1.1: configuration #1 chosen from 1 choice
[1044193.465328] Initializing USB Mass Storage driver...
[1044193.470446] scsi2 : SCSI emulation for USB Mass Storage devices
[1044193.470600] usbcore: registered new interface driver usb-storage
[1044193.470605] USB Mass Storage support registered.
[1044193.470743] usb-storage: device found at 6
[1044193.470745] usb-storage: waiting for device to settle before scanning
[1044198.488028] usb-storage: device scan complete
[1044198.540535] scsi 2:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 0 CCS
[1044200.188400] sd 2:0:0:0: [sdb] 8060928 512-byte hardware sectors: (4.12 GB/3.84 GiB)
[1044200.191395] sd 2:0:0:0: [sdb] Write Protect is off
[1044200.191399] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[1044200.191403] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[1044200.202615] sd 2:0:0:0: [sdb] 8060928 512-byte hardware sectors: (4.12 GB/3.84 GiB)
[1044200.205400] sd 2:0:0:0: [sdb] Write Protect is off
[1044200.205406] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[1044200.205409] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[1044200.205422]  sdb: sdb1
[1044200.276522] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[1044200.276635] sd 2:0:0:0: Attached scsi generic sg2 type 0

```
Now I just need to figure out how to do something smart after it auto-mounts.  My first inclination is to try to find a way to manipulate the "usbcore" or "usb-storage" routine, if I can find out how to configure either.

---

