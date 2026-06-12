---
title: "Having an issue mounting a usb flash drive"
date: 2009-10-03
forum: Hardware
---

### Post by bitchballs on 2009-10-03
Earlier I was experimenting with creating an encrypted usb drive but found a better idea for what I needed.  I had been following a guide in the community documentation and gotten as far as entering the following

```

sudo badblocks -c 10240 -s -w -t random -v /dev/sdb

sudo fdisk /dev/sdb

```

fdisk asks you to confirm writing a DOS disklabel to the drive, which I did.
As per the guide I then used fdisk again, and it asked for some input about the partitions to be created.  I was in the middle of of doing this and started reading something else.  I lost track of what I was doing and had found a better way to handle what I was trying to accomplish with the usb stick in the first place and yanked it out of the port.  Big mistake.  Now the usual automounting seems not to work and neither does manually mounting.

I don't know if this will help but dmesg | tail -20 gives:

[30154.206902]  sdb:            
[30366.011543] usb 2-4: USB disconnect, address 10                                                
[30367.913079] usb 2-4: new high speed USB device using ehci_hcd and address 11                   
[30368.045779] usb 2-4: configuration #1 chosen from 1 choice                                     
[30368.072662] scsi12 : SCSI emulation for USB Mass Storage devices
[30368.079269] usb-storage: device found at 11
[30368.079274] usb-storage: waiting for device to settle before scanning
[30373.076460] usb-storage: device scan complete
[30373.077098] scsi 12:0:0:0: Direct-Access     SanDisk  U3 Titanium      3.27 PQ: 0 ANSI: 2
[30373.093426] sd 12:0:0:0: [sdb] 8027790 512-byte hardware sectors: (4.11 GB/3.82 GiB)
[30373.094685] sd 12:0:0:0: [sdb] Write Protect is off
[30373.094692] sd 12:0:0:0: [sdb] Mode Sense: 0300 00 00
[30373.094697] sd 12:0:0:0: [sdb] Assuming drivecache: write through
[30373.106107] sd 12:0:0:0: [sdb] 8027790 512-byte hardware sectors: (4.11 GB/3.82 GiB)
[30373.129242] sd 12:0:0:0: [sdb] Write Protect is off
[30373.129250] sd 12:0:0:0: [sdb] Mode Sense: 0300 00 00
[30373.129255] sd 12:0:0:0: [sdb] Assuming drivecache: write through
[30373.129263]  sdb:
[30373.130696] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[30373.130832] sd 12:0:0:0: Attached scsi generic sg2 type 0


Also, trying  mount /dev/sdb gets:

mount: can't find /dev/sdb in /etc/fstab or /etc/mtab


I'm assuming I damaged the partition table on the stick since ubuntu seems to be recognizing the hardware fine.  All the information above is accurate and describes the stick.  Is there a way to recover the stick or maybe find out if that is really the problem?

---

### Post by bitchballs on 2009-10-03
Nevermind.  Figured it out.

---

