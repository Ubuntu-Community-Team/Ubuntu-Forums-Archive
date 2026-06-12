---
title: "Can't access USB drives (flash, external enclosures)"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by stuporglue on 2007-02-19
I just got a CompaQ Presario SR2170NX. USB is working for the mouse just fine, but neither my external USB hard drive nor my 7-in-one card reader are working. Both devices work just fine on an OSX machine, as well as on other Edgy installs. I am running Edgy with all updates. 

Symptoms: 

* If the drive mounts at all, any attempt at accessing files on a drive results in that process locking up. Copying files (cp) and removing files (rm) fails. 
* Listing files (ls) seems to work fine. 
* lspci reports the devices fine, but lsusb locks up. 
* A USB optical mouse works fine. 
* "sudo fdisk -l /dev/sdb" locks up
* Since it wasn't working anyways I tried insmodding all USB modules to see if It would load a driver (like so "for i in `modprobe -l | grep usb`; do sudo insmod $i;done"). This also froze up. 


By "locks up" I mean that I cannot interact with the process or terminal any more.  I can close the terminal, and open another, but that's it. Sleeping (^z) and killing (via ^c or kill PID) do nothing. 

Info: 

USB related parts of lspci -v

```
00:13.0 USB Controller: ATI Technologies Inc Unknown device 4387 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 3
        Memory at ff6fe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc Unknown device 4388 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at ff6fd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc Unknown device 4389 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at ff6fc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc Unknown device 438a (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc Unknown device 438b (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at ff6fa000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc Unknown device 4386 (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at ff6ff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port


```

Output of uname -a
```
Linux Elements 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
```

And here is the relavant section of the demsg output:

```
[17179678.716000] usb 6-4: new high speed USB device using ehci_hcd and address 4
[17179678.856000] usb 6-4: configuration #1 chosen from 1 choice
[17179678.856000] hub 6-4:1.0: USB hub found
[17179678.856000] hub 6-4:1.0: 4 ports detected
[17179679.168000] usb 6-4.1: new high speed USB device using ehci_hcd and address 5
[17179679.268000] usb 6-4.1: configuration #1 chosen from 1 choice
[17179679.268000] scsi5 : SCSI emulation for USB Mass Storage devices
[17179679.268000] usb-storage: device found at 5
[17179679.268000] usb-storage: waiting for device to settle before scanning
[17179679.476000] usb 6-4.2: new full speed USB device using ehci_hcd and address 6
[17179679.592000] usb 6-4.2: configuration #1 chosen from 1 choice
[17179684.268000] usb-storage: device scan complete
[17179684.396000]   Vendor: ICSI      Model: CF Card       CF  Rev: 1.8D
[17179684.396000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179684.408000]   Vendor: ICSI      Model: MS Card       MS  Rev: 1.8D
[17179684.408000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179684.420000]   Vendor: ICSI      Model: SD Card   MMC/SD  Rev: 1.8D
[17179684.420000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179684.420000]   Vendor: ICSI      Model: Combo Card    SM  Rev: 1.8D
[17179684.420000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179684.424000] SCSI device sdc: 2001888 512-byte hdwr sectors (1025 MB)
[17179684.424000] sdc: Write Protect is off
[17179684.424000] sdc: Mode Sense: 4b 00 00 08
[17179684.424000] sdc: assuming drive cache: write through
[17179684.428000] SCSI device sdc: 2001888 512-byte hdwr sectors (1025 MB)
[17179684.428000] sdc: Write Protect is off
[17179684.428000] sdc: Mode Sense: 4b 00 00 08
[17179684.428000] sdc: assuming drive cache: write through
[17179684.428000]  sdc: sdc1
[17179684.452000] sd 5:0:0:0: Attached scsi removable disk sdc
[17179684.452000] sd 5:0:0:0: Attached scsi generic sg2 type 0
[17179684.516000] sd 5:0:0:1: Attached scsi removable disk sdd
[17179684.516000] sd 5:0:0:1: Attached scsi generic sg3 type 0
[17179684.588000] sd 5:0:0:2: Attached scsi removable disk sde
[17179684.588000] sd 5:0:0:2: Attached scsi generic sg4 type 0
[17179684.596000] sd 5:0:0:3: Attached scsi removable disk sdf
[17179684.596000] sd 5:0:0:3: Attached scsi generic sg5 type 0
[17179685.280000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179755.588000] usb 6-4: USB disconnect, address 4
[17179755.588000] usb 6-4.1: USB disconnect, address 5

```

Both the rear and front panel USB ports behave the same way.



EDIT/UPDATE:
The USB drives work just fine in Windows Vista on this machine, so all pieces of hardware seem to be working and accounted for.

---

