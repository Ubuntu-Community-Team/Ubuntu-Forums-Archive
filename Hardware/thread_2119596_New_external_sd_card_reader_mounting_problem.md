---
title: "New external sd card reader mounting problem"
date: 2013-02-24
forum: Hardware
---

### Post by dr-kart on 2013-02-24
Ubuntu 12.10x64 can not mount external usb card reader with sd card, FAT32 formatted. Win7 opens and operates it with no problem at all. 

Gparted CAN see device but says about mounting problem. See pics.

[[IMG]http://storage5.static.itmages.ru/i/13/0224/s_1361715350_6620724_5ffb43bb42.png[/IMG]]("http://itmages.ru/image/view/911605/5ffb43bb")

[[IMG]http://storage6.static.itmages.ru/i/13/0224/s_1361715435_5336756_3a6c7daef1.png[/IMG]]("http://itmages.ru/image/view/911606/3a6c7dae")

The same symptoms in 12.04.1. Help.

---

### Post by thermion on 2013-02-24
That's strange...
Could you post the output of:

```
dpkg -l | grep 'dosfstools\|mtools'
```

---

### Post by dr-kart on 2013-02-24
dpkg -l | grep 'dosfstools\|mtools'
```

ii  dosfstools                                3.0.13-1                                  amd64        utilities for making and checking MS-DOS FAT filesystems
ii  mtools                                    4.0.17-1                                  amd64        Tools for manipulating MSDOS files

```

---

### Post by thermion on 2013-02-24
Connect your sdcard to your computer and post the output of:

```
tail -n 20 /var/log/syslog
```

---

### Post by dr-kart on 2013-02-24
tail -n 20 /var/log/syslog
```

Feb 24 19:01:23 dipk kernel: [ 8938.159225] scsi 9:0:0:0: Direct-Access     TS-RDF5  SD  Transcend    TS32 PQ: 0 ANSI: 5
Feb 24 19:01:23 dipk kernel: [ 8938.160032] sd 9:0:0:0: Attached scsi generic sg2 type 0
Feb 24 19:01:23 dipk kernel: [ 8938.338439] sd 9:0:0:0: [sdb] 30702592 512-byte logical blocks: (15.7 GB/14.6 GiB)
Feb 24 19:01:23 dipk kernel: [ 8938.339548] sd 9:0:0:0: [sdb] Write Protect is off
Feb 24 19:01:23 dipk kernel: [ 8938.339550] sd 9:0:0:0: [sdb] Mode Sense: 21 00 00 00
Feb 24 19:01:23 dipk kernel: [ 8938.340670] sd 9:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb 24 19:01:23 dipk kernel: [ 8938.601810] sd 9:0:0:0: [sdb]  
Feb 24 19:01:23 dipk kernel: [ 8938.601814] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 24 19:01:23 dipk kernel: [ 8938.601815] sd 9:0:0:0: [sdb]  
Feb 24 19:01:23 dipk kernel: [ 8938.601816] Sense Key : Aborted Command [current] 
Feb 24 19:01:23 dipk kernel: [ 8938.601818] sd 9:0:0:0: [sdb]  
Feb 24 19:01:23 dipk kernel: [ 8938.601819] Add. Sense: Data phase CRC error detected
Feb 24 19:01:23 dipk kernel: [ 8938.601821] sd 9:0:0:0: [sdb] CDB: 
Feb 24 19:01:23 dipk kernel: [ 8938.601821] Read(10): 28 00 00 00 00 00 00 00 08 00
Feb 24 19:01:23 dipk kernel: [ 8938.601825] end_request: I/O error, dev sdb, sector 0
Feb 24 19:01:23 dipk kernel: [ 8938.601828] Buffer I/O error on device sdb, logical block 0
Feb 24 19:01:24 dipk kernel: [ 8938.854147] ldm_validate_partition_table(): Disk read failed.
Feb 24 19:01:24 dipk kernel: [ 8938.854154] Dev sdb: unable to read RDB block 0
Feb 24 19:01:24 dipk kernel: [ 8938.855485]  sdb: unable to read partition table
Feb 24 19:01:24 dipk kernel: [ 8938.859997] sd 9:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by thermion on 2013-02-24
If this sdcard is empty, go to gparted and create a new partitiontable (msdos) and a new fat32 partition.

---

### Post by dr-kart on 2013-02-24
I did that before. Gparted created fat32 partition. And I was able to write on flash. But when I unmount and mount device I get same error. While no errors on Win.

Edit: after gparted formated (fat32) sd card I put some files on it. No error messages on ubuntu. But then I checked it on Win and saw NO FILES on it! So data writing was failed on ubuntu.

---

### Post by thermion on 2013-02-24
The problem here is not the partition, rather than the partition table itself.
Have you tried to create a new partition table?

```
19:01:24 dipk kernel: [ 8938.855485]  sdb: unable to read partition table
```

---

### Post by dr-kart on 2013-02-24
> **thermion said:**
>  ...Have you tried to create a new partition table?



Just did it with creatian new partition table (msdos type) first. All the same. Creation successful.After unmount and mount again I get same:
```

Feb 24 20:02:58 dipk kernel: [  511.549030] scsi 8:0:0:0: Direct-Access     TS-RDF5  SD  Transcend    TS32 PQ: 0 ANSI: 5
Feb 24 20:02:58 dipk kernel: [  511.549955] sd 8:0:0:0: Attached scsi generic sg2 type 0
Feb 24 20:02:58 dipk kernel: [  511.713754] sd 8:0:0:0: [sdb] 30702592 512-byte logical blocks: (15.7 GB/14.6 GiB)
Feb 24 20:02:58 dipk kernel: [  511.714878] sd 8:0:0:0: [sdb] Write Protect is off
Feb 24 20:02:58 dipk kernel: [  511.714880] sd 8:0:0:0: [sdb] Mode Sense: 21 00 00 00
Feb 24 20:02:58 dipk kernel: [  511.715982] sd 8:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb 24 20:02:59 dipk kernel: [  512.005057] sd 8:0:0:0: [sdb]  
Feb 24 20:02:59 dipk kernel: [  512.005060] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 24 20:02:59 dipk kernel: [  512.005061] sd 8:0:0:0: [sdb]  
Feb 24 20:02:59 dipk kernel: [  512.005062] Sense Key : Aborted Command [current] 
Feb 24 20:02:59 dipk kernel: [  512.005064] sd 8:0:0:0: [sdb]  
Feb 24 20:02:59 dipk kernel: [  512.005066] Add. Sense: Data phase CRC error detected
Feb 24 20:02:59 dipk kernel: [  512.005068] sd 8:0:0:0: [sdb] CDB: 
Feb 24 20:02:59 dipk kernel: [  512.005068] Read(10): 28 00 00 00 00 00 00 00 08 00
Feb 24 20:02:59 dipk kernel: [  512.005072] end_request: I/O error, dev sdb, sector 0
Feb 24 20:02:59 dipk kernel: [  512.005075] Buffer I/O error on device sdb, logical block 0
Feb 24 20:02:59 dipk kernel: [  512.266018] ldm_validate_partition_table(): Disk read failed.
Feb 24 20:02:59 dipk kernel: [  512.266033] Dev sdb: unable to read RDB block 0
Feb 24 20:02:59 dipk kernel: [  512.267497]  sdb: unable to read partition table
Feb 24 20:02:59 dipk kernel: [  512.271447] sd 8:0:0:0: [sdb] Attached SCSI removable disk


```

---

### Post by thermion on 2013-02-24
Well, there's still this line:

```
Feb 24 20:02:59 dipk kernel: [  512.005066] Add. Sense: Data phase CRC error detected
```

Windows tends to ignore hardware errors to a certain point. Do you have a second sdcard you could plug in to your card reader just to see if this behaviour can be reproduced?

---

### Post by dr-kart on 2013-02-24
!!!
Card reader is for sd and micro sd cards. I placed my micro sd card into adapter. And I plugged reader with micro sd with SD adapter. IT WORKS. And it doesn't work with micro sd inserted without SD adapter.

Just can't figure out why it happens. :confused:

---

### Post by thermion on 2013-02-24
So, when you are using a microSD adapter you are able to mount the card?
Do you have another card reader? I can't imagine that the sdcard is damaged.

---

### Post by dr-kart on 2013-02-24
> **thermion said:**
> 
Do you have another card reader? 
no I don't 

reader and micro sd card are brand new.

It looks like my reader can not work with micro sd correctly

Anyway, **[[COLOR=#000000]thermion[/COLOR]]("http://ubuntuforums.org/member.php?u=1781543")** thanks for the help!!!!!!

---

### Post by thermion on 2013-02-24
You're welcome.
Just because both are new doesn't mean they can't be faulty in some way.

But the only way to make sure is to either replace the cardreader or the actual sdcard.

---

### Post by dr-kart on 2013-02-24
Due to the fact of correct functioning (with no errors on Linux) via SD Adapter, I think I rather have faulty micro sd slot in my reader than sd card. No?

---

### Post by thermion on 2013-02-24
That's my guess. This can only be verified by using another sdcard or by temporarily replacing the card reader

---

