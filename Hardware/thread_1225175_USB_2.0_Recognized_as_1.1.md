---
title: "USB 2.0 Recognized as 1.1"
date: 2009-07-28
forum: Hardware
---

### Post by Otustelija on 2009-07-28
I'm trying to get my Anysee E30 DVB-T USB device working with Ubuntu Jaunty 64. It requires a USB 2.0 port, which all of the ports on my ASUS M3N78-EM are. However, plugging it in, this is the output from dmesg:

```
[ 2856.872543] usb 2-5: new high speed USB device using ehci_hcd and address 15
[ 2856.928770] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 2857.172032] usb 2-5: new high speed USB device using ehci_hcd and address 16
[ 2857.228784] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 2857.620057] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 2857.988524] usb 2-5: new high speed USB device using ehci_hcd and address 18
[ 2858.044357] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 2858.500033] usb 4-5: new full speed USB device using ohci_hcd and address 14
[ 2859.440611] usb 4-5: not running at top speed; connect to a high speed hub
[ 2859.455699] usb 4-5: configuration #1 chosen from 1 choice
[ 2859.460815] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[ 2859.460851] dvb-usb: This USB2.0 device cannot be run on a USB1.1 port. (it lacks a hardware PID filter)
[ 2859.460879] dvb-usb: Anysee DVB USB2.0 error while loading driver (-19)
```

It seems that it thinks it a 1.1 port, as it is using ohci_hcd? The exact same port works fine with SanDisk Cruzer:

```
[ 3165.884525] usb 2-5: new high speed USB device using ehci_hcd and address 19
[ 3166.018298] usb 2-5: configuration #1 chosen from 1 choice
[ 3166.028563] scsi9 : SCSI emulation for USB Mass Storage devices
[ 3166.029819] usb-storage: device found at 19
[ 3166.029822] usb-storage: waiting for device to settle before scanning
[ 3171.028756] usb-storage: device scan complete
[ 3171.030485] scsi 9:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[ 3171.032123] sd 9:0:0:0: [sdb] 8027793 512-byte hardware sectors: (4.11 GB/3.82 GiB)
[ 3171.033862] sd 9:0:0:0: [sdb] Write Protect is off
[ 3171.033866] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3171.033870] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3171.053716] sd 9:0:0:0: [sdb] 8027793 512-byte hardware sectors: (4.11 GB/3.82 GiB)
[ 3171.054332] sd 9:0:0:0: [sdb] Write Protect is off
[ 3171.054335] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3171.054338] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3171.054344]  sdb: sdb1
[ 3171.055753] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 3171.055829] sd 9:0:0:0: Attached scsi generic sg2 type 0
```

Any ideas how to proceed?

---

### Post by nomnex on 2010-04-06
Similar issue here on a FMV-BIBLO NH28D: 4 USB2 ports on this notebook. Ubuntu 9.10 sees 3 USB1 and 1 USB2 ports.

From a IRC chat session, it could be a motherboard issue? I'll wait to install 10.04, end of this month before opening a bug on Launchpad to troubleshoot the issue.

I will past the link for reference along the thread.

---

