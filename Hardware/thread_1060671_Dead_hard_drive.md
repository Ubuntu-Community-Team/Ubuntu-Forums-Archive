---
title: "Dead hard drive?"
date: 2009-02-05
forum: Hardware
---

### Post by austin987 on 2009-02-05
Howdy,

Turned computer on today to find a flood of error messages about SDA3 (DRDY ERR). I unfortunately don't have a full log (may get one soon). No errors/clicking sounds/etc. were present before. Only recent error was the hard drive had hit capacity a week or so ago, so I emptied trash/deleted some files, and all was well.

After a bit of debugging, seems the drive is either A) corrupted massively or B) dying. Trying to boot from a livecd takes forever, as each step is slowed down by the flood of errors in dmesg. I was able to get a feisty alternate install cd to get to a repair console, and found that the partition table is okay, but the main partition isn't listed. There were 5 partitions (IIRC, 3 actual partitions, maybe 4, but at least one was the logical partition).

'fdisk -l' shows the drive and all partitions. 'ls /dev/sd*', however, shows sda1, sda2, sda4, and sda5 (sda3 being the partition I need). Tried 'fsck.ext3 /dev/sda3' which says partition not found. Trying it on the other partitions gives an error that the superblock can't be found.

Lastly, I tried doing a dd backup to an external drive, but that gives me several 'dd: /dev/sda: Input/output error' errors, then dies at about 4.6G in (drive is 160GB).

Exact dd command used was 'dd bs=512 if=/dev/sda3 of=/media/disk/foo.img conv=noerror,sync" which should've skipped over errors and filled it with NULL.

I've now pulled the drive out, to get it out of the heat. I'm thinking of trying the freezer trick, and then running dd again, or possibly putting it in a windows box and then using dd for windows (hopefully since it's ext3 formatted windows won't try to mount it and fail).

The drive isn't massively important, I've filled out the RMA form, and it's replaceable. But there are some vacation pictures that I need to recover, as well as some documents, etc.

Any advice appreciated.

---

### Post by halovivek on 2009-02-05
Boot the system from live CD and check the problem by scanning the hard disk for problem.

---

### Post by austin987 on 2009-02-05
LiveCD gives the kernel errors I previously mentioned. /dev/sda3 is not available, so I can't run fsck on it.

---

### Post by austin987 on 2009-02-05
Got a hold of an external enclosure. Dmesg output when plugged in (full output attached):

```

[62399.253328] scsi 8:0:0:0: Direct-Access     ST316082 7AS                   PQ: 0 ANSI: 2 CCS
[62399.301269] sd 8:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[62399.302703] sd 8:0:0:0: [sdc] Write Protect is off
[62399.302710] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00
[62399.302713] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[62399.303802] sd 8:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[62399.304681] sd 8:0:0:0: [sdc] Write Protect is off
[62399.304684] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00
[62399.304687] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[62399.305021]  sdc: sdc1 < sdc5 > sdc2 sdc3 sdc4
[62399.343807] sd 8:0:0:0: [sdc] Attached SCSI disk
[62399.344252] sd 8:0:0:0: Attached scsi generic sg3 type 0
[62403.371405] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[62403.371415] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
[62403.371419] sd 8:0:0:0: [sdc] Add. Sense: Unrecovered read error
[62403.371424] end_request: I/O error, dev sdc, sector 39070080
[62403.371433] Buffer I/O error on device sdc3, logical block 0
[62403.371437] Buffer I/O error on device sdc3, logical block 1
[62403.371440] Buffer I/O error on device sdc3, logical block 2
[62403.371443] Buffer I/O error on device sdc3, logical block 3
[62403.371445] Buffer I/O error on device sdc3, logical block 4
[62403.371448] Buffer I/O error on device sdc3, logical block 5
[62403.371451] Buffer I/O error on device sdc3, logical block 6
[62403.371453] Buffer I/O error on device sdc3, logical block 7
[62403.371458] Buffer I/O error on device sdc3, logical block 8
[62403.371461] Buffer I/O error on device sdc3, logical block 9
```


attempting to run fsck on it (shows the partition this time!):
austin@austin-desktop:~$ sudo fsck.ext3 /dev/sdc3
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc3
Could this be a zero-length partition?

Running a dd now, hopefully it'll get further this time.

---

### Post by Yannick Le Saint kyncani on 2009-02-05
The disk looks dead all right. You may try ddrescue (in package gddrescue) instead of dd and then photorec to try and recover some files.

Also leaving the disk cool down or something and try again later.

I would not place to much hope in recovering anything at all though (hope you have backup).

---

### Post by austin987 on 2009-02-07
> **Yannick Le Saint kyncani said:**
> The disk looks dead all right. You may try ddrescue (in package gddrescue) instead of dd and then photorec to try and recover some files.

Also leaving the disk cool down or something and try again later.

I would not place to much hope in recovering anything at all though (hope you have backup).


Worked well. Took about 33 hours (!) to run on a 140 GB partition. There are two more partitions on the drive, 10 GB each. It succeeded in ddrescue'ing both, but one of them still won't fsck (it was the os partition), the second I haven't tried yet, still finishing up ddrescue.

The 140 GB partition was the important one, had my /home folder. It lost about 8 MB, not that big of deal. Looking around, most of my important files are there, not sure what all was lost, but couldn't have been too much.

Thanks for the advice! I was under the impression that dd would skip over errors with the 'noerror' option, but seems I was wrong. Good to know.

Now to RMA the drive and send the FSF a donation for hosting ddrescue :-).

---

### Post by austin987 on 2009-02-07
Adding resolved tag...not sure if that's the right policy or not, seems to be popular at least.

If it's not, please let me know.

---

