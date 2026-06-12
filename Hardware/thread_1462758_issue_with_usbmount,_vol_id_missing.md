---
title: "issue with usbmount, vol_id missing"
date: 2010-04-26
forum: Hardware
---

### Post by garforez on 2010-04-26
Hello, 

I'm facing an issue with the automatic mounting of external usb drives via usbmount.
The drives themseves don't seem to have any issues as I can mount them manualy.

Please note that this behaviour was introduced by the installation of the gtkpod and underlying dependecies, and that before this operation usb auto mount worked perfectly ( desinstalling the packages did not fix the issue ).

So currently, when I connect an usb key to my laptop, I get the following messages in the syslog : 

```

Apr 26 08:57:40 zmac kernel: [ 1654.924047] usb 2-2: new high speed USB device using ehci_hcd and address 4
Apr 26 08:57:40 zmac kernel: [ 1655.059725] usb 2-2: configuration #1 chosen from 1 choice
Apr 26 08:57:40 zmac kernel: [ 1655.059963] scsi8 : SCSI emulation for USB Mass Storage devices
Apr 26 08:57:40 zmac kernel: [ 1655.066779] usb-storage: device found at 4
Apr 26 08:57:40 zmac kernel: [ 1655.066782] usb-storage: waiting for device to settle before scanning
Apr 26 08:57:45 zmac kernel: [ 1660.064284] usb-storage: device scan complete
Apr 26 08:57:45 zmac kernel: [ 1660.092384] scsi 8:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Apr 26 08:57:45 zmac kernel: [ 1660.092962] sd 8:0:0:0: Attached scsi generic sg4 type 0
Apr 26 08:57:46 zmac kernel: [ 1660.850875] sd 8:0:0:0: [sdd] 15646720 512-byte logical blocks: (8.01 GB/7.46 GiB)
Apr 26 08:57:46 zmac kernel: [ 1660.851727] sd 8:0:0:0: [sdd] Write Protect is off
Apr 26 08:57:46 zmac kernel: [ 1660.851731] sd 8:0:0:0: [sdd] Mode Sense: 23 00 00 00
Apr 26 08:57:46 zmac kernel: [ 1660.851734] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Apr 26 08:57:46 zmac kernel: [ 1660.855732] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Apr 26 08:57:46 zmac kernel: [ 1660.855748]  sdd: sdd1
Apr 26 08:57:46 zmac kernel: [ 1660.879735] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Apr 26 08:57:46 zmac kernel: [ 1660.879740] sd 8:0:0:0: [sdd] Attached SCSI removable disk
Apr 26 08:57:46 zmac usbmount[3647]: cannnot execute /lib/udev/vol_id
Apr 26 08:57:46 zmac usbmount[3661]: cannnot execute /lib/udev/vol_id

```

I checked and was unable to find /lib/udev/vol_id on my drive. I don't know what this binary is nor  how to install it.

If anyone has any info on this binary or ides on how to solve the usbmount issue, I'd be realy gratfull.

Thanks, 

PS , my setup info : 

- Ubuntu 9.10 desktop
- usbmount v 0.0.17

---

