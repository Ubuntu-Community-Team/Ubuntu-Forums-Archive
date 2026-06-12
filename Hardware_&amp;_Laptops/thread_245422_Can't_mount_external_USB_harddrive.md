---
title: "Can't mount external USB harddrive"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by wr0x2 on 2006-08-27
I have a 300gb sata disk in a usb enclosure. Long story short, I partially formatted the drive but recovered most of what was on it with e2fsck, which dumped everything into lost+found. Anyway, a little while I tried to write to the drive on another machine and now it doesn't work at all... Here's the relevant output from dmesg:

```

[17180742.076000] usb 1-1: new high speed USB device using ehci_hcd and address 3
[17180742.432000] Initializing USB Mass Storage driver...
[17180742.432000] scsi2 : SCSI emulation for USB Mass Storage devices
[17180742.432000] usb-storage: device found at 3
[17180742.432000] usb-storage: waiting for device to settle before scanning
[17180742.432000] usbcore: registered new driver usb-storage
[17180742.432000] USB Mass Storage support registered.
[17180747.432000]   Vendor: SAMSUNG   Model: S01XJ10XC14834    Rev: SW10
[17180747.432000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180747.432000] SCSI device sdc: 312581808 512-byte hdwr sectors (160042 MB)
[17180747.432000] sdc: assuming drive cache: write through
[17180747.432000] SCSI device sdc: 312581808 512-byte hdwr sectors (160042 MB)
[17180747.432000] sdc: assuming drive cache: write through
[17180747.432000]  sdc:<6>usb 1-1: reset high speed USB device using ehci_hcd and address 3
[17180787.788000] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[17180824.032000] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[17180824.144000] usb 1-1: device descriptor read/64, error -71
[17180824.360000] usb 1-1: device descriptor read/64, error -71
[17180824.576000] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[17180824.688000] usb 1-1: device descriptor read/64, error -71
[17180824.904000] usb 1-1: device descriptor read/64, error -71
[17180825.120000] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[17180825.528000] usb 1-1: device not accepting address 3, error -71
[17180825.640000] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[17180826.048000] usb 1-1: device not accepting address 3, error -71
[17180826.048000] usb 1-1: USB disconnect, address 3
[17180826.048000] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery
[17180826.048000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17180826.048000] end_request: I/O error, dev sdc, sector 0
[17180826.048000] Buffer I/O error on device sdc, logical block 0
[17180826.048000] sd 2:0:0:0: rejecting I/O to offline device
[17180826.048000] Buffer I/O error on device sdc, logical block 0
[17180826.048000]  unable to read partition table

```

The device can't even connect, what's up here?

---

### Post by wr0x2 on 2006-09-04
A little additional info...

I have a 160 gb drive in there actually, not my damaged 320. I didn't even read the output from dmesg...

Anyway, the drive is formatted in one ext2 partition, and was working fine inside my computer, although I was never able to access it from windows using  a windows ext2 driver...

---

### Post by dysentry on 2007-12-01
```

[17180825.120000] usb 1-1: reset high speed USB device using **ehci_hcd** and address 3
[17180825.528000] usb 1-1: device not accepting address 3, error -71

```

I had a similar problem, one of my external hard disks would work, other times it would not.

When it did work, it would unmount/disappear after about an hour of unactivity.

How I got it working was by running:

rmmod ehci_hcd

Problem appears to be with with it trying to run it at high speed rather than full speed.

All your usb devices will remount after you run this command, so it isn't wise to do it when you are accessing them.


Below is some more information:

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg13828.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg13828.html)

---

### Post by ev5unleash1 on 2007-12-01
Looks like to me, What he said, the System is trying to run at High Speed that may be higher than the current devices Max speed.

---

