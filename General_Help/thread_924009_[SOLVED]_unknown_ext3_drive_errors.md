---
title: "[SOLVED] unknown ext3 drive errors"
date: 2008-09-19
forum: General Help
---

### Post by DiGiTY on 2008-09-19
I just put in a 2 TB RAID setup (Adaptec 2410SA 4 port SATA RAID controller with 2 x 1 TB Samsung HD103UJ SATA hard drives). Formatted it as EXT3, kicked off a huge transfer of 900 GB (using cp command) and walked away. Came back to find Ubuntu (7.10) restarted and obviously only some of my files were transferred

Checked the system log (/var/log/messages) and these errors popped out to me:

```

Sep 18 19:59:11 phyrehouse kernel: [ 8648.699930] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699937] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699943] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699949] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699955] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699961] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699975] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK
Sep 18 19:59:11 phyrehouse kernel: [ 8648.699984] end_request: I/O error, dev sdb, sector 251399
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700016] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700024] end_request: I/O error, dev sdb, sector 251535
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700053] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700061] end_request: I/O error, dev sdb, sector 251671
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700081] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700088] end_request: I/O error, dev sdb, sector 251807
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700098] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700104] end_request: I/O error, dev sdb, sector 251815
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700117] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700124] end_request: I/O error, dev sdb, sector 3563323455
Sep 18 19:59:11 phyrehouse kernel: [ 8648.700308] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.701718] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702075] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702086] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702096] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702107] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702117] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702128] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702139] lost page write due to I/O error on sdb1
Sep 18 19:59:11 phyrehouse kernel: [ 8648.702149] lost page write due to I/O error on sdb1
Sep 18 20:02:08 phyrehouse syslogd 1.4.1#21ubuntu3: restart.
```

these messages occurred right in the middle of copying those files and right before Ubuntu restarted. sdb1 is the 2 TB RAID drive (drive in question)

any idea why this is happening and how to resolve it?

---

### Post by fjgaude on 2008-09-19
Your raid setup, raid1 or raid0?

From the errors it looks like a bad drive, but what do I know? <smile>

---

### Post by DiGiTY on 2008-09-21
RAID-0. brand new drives

---

### Post by fjgaude on 2008-09-22
Somehow you have to test the array with **fsck**... the array has to be unmounted.

But first simply try this:

```
sudo fdisk -l
```

to see if the two drives look okay. Then:

```
sudo fsck -t ext3 /dev/md[n]
```

If that shows no issues, then mount array and do:

```
sudo mdadm -D /dev/md[n]
```

Let us know how things go.

---

### Post by Jonie on 2008-09-22
> RAID-0. brand new drives

It happens. The sequence of errors (interleaved with good sectors from the other drive) looks like one of the drives is faulty. I think you need replacement.

Disconnect the array (connect the drives to the onboard controller) and check the drives for hardware defects. You may run smartctl -a to tell if there are any Reallocated Sectors, Current Pending Sector or Offline Uncorrectable.


@fjgaude: it doesn't use mdadm. It's a hardware RAID.

---

### Post by fjgaude on 2008-09-22
Sorry about that... hardware, then it could be the controller board.

Try this:

sudo fsck.ext3 -f /dev/<device>

That will force check the array... but as was said, one or more of your drives could be bad.

---

### Post by DiGiTY on 2008-09-26
i ended up just re-formatting the drives from the RAID setup utility (which I didn't do before), then creating the array then initializing with gparted, then formatting with mkfs.ext3.

been running 4 days without a problem. previously it ran into those errors after 8 or so hours

i also didn't have the SATA controller securely seated in the PCI slot. that may have actually been the culprit

---

### Post by fjgaude on 2008-09-26
Okay, happy you have made progress... hope everything continues to work correctly.

---

