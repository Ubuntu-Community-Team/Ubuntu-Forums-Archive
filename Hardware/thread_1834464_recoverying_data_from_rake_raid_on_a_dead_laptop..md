---
title: "recoverying data from rake raid on a dead laptop."
date: 2011-08-27
forum: Hardware
---

### Post by pinan on 2011-08-27
I have a laptop( sony running unbunt 10) with data installed on a  raid 1 setup, the lap top has died.  I would like to recover the data from the disks. I have been able to plug the disk in to a desktop system using a  state hard drive mount adaptor.

Doing an fdisk -l reports the drive, but list it as an unknown partition table[ a dmesg dump is given at the end].

The dive is a Fujitsu as listed by dmesg, so I am assuming from this that the drive is ok and that the data is laid out as a raid file system.  I had assumed that use of raid 1 disk would result in the contents off disk 0 being the same as disk 1.
My question is what options should I quote to things like fdisk to be able to tell it do understand the format of the disk. 
 The laptop is about 3 years and for the cost of getting it repaired,  I could have a much faster machine, hence the interest in just getting access to the contents of the disks.

Any suggestion as to what to do next?

dmesg dump
=======================================================================
[  613.940045] usb 1-5: new high speed USB device using ehci_hcd and address 6
[  614.073683] usb-storage 1-5:1.0: Quirks match for vid 152d pid 2329: 8020
[  614.073736] scsi8 : usb-storage 1-5:1.0
[  615.072653] scsi 8:0:0:0: Direct-Access     FUJITSU  MHX2250BT             PQ: 0 ANSI: 2 CCS
[  615.073684] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  615.074997] sd 8:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[  615.075912] sd 8:0:0:0: [sdb] Write Protect is off
[  615.075919] sd 8:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  615.075924] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  615.079388] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  615.110042]  sdb: unknown partition table
[  615.112992] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  615.113000] sd 8:0:0:0: [sdb] Attached SCSI disk
[  649.330660] usb 1-5: USB disconnect, address 6
[  670.036035] usb 1-5: new high speed USB device using ehci_hcd and address 7
[  670.169705] usb-storage 1-5:1.0: Quirks match for vid 152d pid 2329: 8020
[  670.169757] scsi9 : usb-storage 1-5:1.0
[  671.168674] scsi 9:0:0:0: Direct-Access     FUJITSU  MHX2250BT             PQ: 0 ANSI: 2 CCS
[  671.169697] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  671.170895] sd 9:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[  671.171912] sd 9:0:0:0: [sdb] Write Protect is off
[  671.171919] sd 9:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  671.171924] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  671.175285] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  671.193935]  sdb: unknown partition table
[  671.195645] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  671.195651] sd 9:0:0:0: [sdb] Attached SCSI disk
[  944.784789] usb 1-5: USB disconnect, address 7

The dive is a Fujitsu, so I am assuming from this that the drive is ok and that the data is laid out as a raid file system.  I had assumed that use of raid 1 disk would result in the contents off disk 0 being the same as disk1.
My question is what options should I quote to things like fdisk to be able to tell it do understand the format of the disk.  The laptop is about 3 years and for the cost of getting it repaired,  I could have a much faster machine, hence the interest in just getting access to the contents of the disks.

Any suggestion as to what to do next?

---

