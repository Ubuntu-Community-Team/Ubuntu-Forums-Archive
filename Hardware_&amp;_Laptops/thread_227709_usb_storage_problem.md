---
title: "usb storage problem"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by termite on 2006-08-02
Hi,

Until a couple of days ago, I had no serious problems with USB storage.  Right now, I can't access any of my USB storage devices.

Here is the problem:
- I insert a USB device (say an external HD).  dmesg|tail gives:
> usb 3-3: new high speed USB device using ehci_hcd and address 4
usb 3-3: configuration #1 chosen from 1 choice
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: Maxtor 6  Model: L300R0            Rev: BAJ4
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete

- No device of the form sda* appears in /dev, so I cannot mount.  Obviously, automount doesn't work.

Any ideas why the sda device doesn't appear?

Here is the output of lsusb:
> Bus 003 Device 004: ID 04cf:8818 Myson Century, Inc. Fast 3.5" External Storage
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

New information: the /dev/sd* devices do appear under the 2.6.15-26-686 kernel.  However, I would very much like them to work under my custom 2.6.17.5 kernel...advice more than welcome.

---

### Post by hw-tph on 2006-08-02
Did you configure your custom kernel manually? I suggest you use the .config (available in /boot as config-$(uname -r)) as a base and then remove/change whatever you want. Make sure you do not remove SCSI disk support and similar drivers that are required for USB storage devices.

I run a locally built 2.6.17-ck1 with no problems whatsoever.


Håkan

---

### Post by termite on 2006-08-02
I have scsi support and all USB storage options compiled into the custom kernel, as far as I know.

---

