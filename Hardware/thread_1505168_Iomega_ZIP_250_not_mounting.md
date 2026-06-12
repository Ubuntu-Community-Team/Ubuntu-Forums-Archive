---
title: "Iomega ZIP 250 not mounting"
date: 2010-06-08
forum: Hardware
---

### Post by stepstools on 2010-06-08
Yah, I still use my 250 megabyte drive.  But in 9.10 it stopped wanting to mount.  I need an answer sort of fast.  Any ideas? :confused:

---

### Post by anglican on 2010-06-09
> **stepstools said:**
> Yah, I still use my 250 megabyte drive.  But in 9.10 it stopped wanting to mount.  I need an answer sort of fast.  Any ideas? :confused:
When you put a disk in what (if anything) shows up in the last few lines of "dmesg"?

H

---

### Post by stepstools on 2010-06-09
Nothing happens when I put a disk in, what's "dmesg"?

---

### Post by stepstools on 2010-06-09
Got Something - 
```
[ 2418.848498] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 07 77 80 00 00 08 00
[ 2418.848527] end_request: I/O error, dev sdb, sector 489344
[ 2418.848540] Buffer I/O error on device sdb, logical block 122336
[ 2418.848549] Buffer I/O error on device sdb, logical block 122337
[ 2644.420063] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 2644.588540] usb 3-1: configuration #1 chosen from 1 choice
[ 2644.607638] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2644.612713] usb-storage: device found at 5
[ 2644.612717] usb-storage: waiting for device to settle before scanning
[ 2649.613389] usb-storage: device scan complete
[ 2649.617382] scsi 7:0:0:0: Direct-Access     IOMEGA   ZIP 250          90.V PQ: 0 ANSI: 0 CCS
[ 2649.623191] sd 7:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by anglican on 2010-06-10
> **stepstools said:**
> Got Something - 
```

[ 2649.617382] scsi 7:0:0:0: Direct-Access     IOMEGA   ZIP 250          90.V PQ: 0 ANSI: 0 CCS
[ 2649.623191] sd 7:0:0:0: Attached scsi generic sg2 type 0

```
OK, it looks like the disk is seen but just not mounted. Try to create a mount point:
```
sudo mkdir /mnt/zip

```Then mount it:
```
sudo mount /dev/sg2 /mnt/zip -o ro
```If you get no error, look at the contents with:
```
ls -l /mnt/zip
```Good luck.

H

---

### Post by stepstools on 2010-06-10
Second command returned this -
```
mount: special device /dev/sg2 does not exist

```

---

### Post by anglican on 2010-06-11
> **stepstools said:**
> Second command returned this -
```
mount: special device /dev/sg2 does not exist

```
Sorry, yes sg2 is wrong it should be sdb1. But this probably still wont work from the looks of your dmesg output. try:
```
sudo modprobe usb-storage
```Then see what dmesg shows. There should be a lines something like:
[ 2649.623191] sdb: sdb1
[ 2649.623191] sd 7:0:0:0: [sdb] Direct-Access     IOMEGA   ZIP 250          90.V PQ: 0 ANSI: 0 CCS
[ 2649.623191] sd 7:0:0:0: Attached scsi generic sg2 type 0

In which case "sudo mount /dev/sdb1 /mnt/zip" should work. But I'm a bit worried by the errors:
> [ 2418.848527] end_request: I/O error, dev sdb, sector 489344
[ 2418.848540] Buffer I/O error on device sdb, logical block 122336
[ 2418.848549] Buffer I/O error on device sdb, logical block 122337Which suggest there may be a problem with your disk.

H

---

### Post by stepstools on 2010-06-11
I will try this later today, but I put in my 8.10 cd and ran it live, and it couldn't find the zip.  The formatting may be not right, what would be the best format?

---

### Post by anglican on 2010-06-14
> **stepstools said:**
> I will try this later today, but I put in my 8.10 cd and ran it live, and it couldn't find the zip.  The formatting may be not right, what would be the best format?

I would have thought it would be best to keep to DOS/VFAT format which is how the disks come formatted originally (or HFS for use with MACs). If you think you'll ever want to use it with a Windows computer that's the only choice. Of course they can be formatted ext2 and probably other ways also.

H

---

