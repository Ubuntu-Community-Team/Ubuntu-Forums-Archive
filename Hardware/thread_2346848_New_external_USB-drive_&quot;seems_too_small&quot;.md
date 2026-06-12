---
title: "New external USB-drive &quot;seems too small&quot; (Testdisk)"
date: 2016-12-19
forum: Hardware
---

### Post by mat14 on 2016-12-19
Hello,

I recently bought a Samsung 2TB USB-disk which only shows 60 GB. I tried to format it in gparted and Windows, but without effect. Testdisk reports the right size but adds "The hard disk seems too small". Doing a partition search finds the formatted 60 GB partition and the 2 TB exFAT but flags it as not recoverable: "The following partitions can't be recovered".
Can anyone tell me how to get the right size back? Anything I do ends up having a 60 GB disk.
The disk is empty, so I can do whatever it takes.

---

### Post by oldfred on 2016-12-19
Some external drives use proprietary configurations to work with XP. 
Better to just make it generic.
I might delete those two partitions. 
If using with Windows just use NTFS, not exFAT, some gaming systems may need exFAT.

I would also use gpt partitioning.
What does this show (if sdb)?
sudo gdisk -l /dev/sdb
        I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

---

### Post by mat14 on 2016-12-20
```
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdb: 117210240 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A6E3CE33-43BA-4AF6-95FE-3EA921D35242
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117210206
Partitions will be aligned on 2048-sector boundaries
Total free space is 117210173 sectors (55.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
```

Clearly the information is faulty. Converted to GPt, but it's still the wrong size. How do I proceed now?

---

### Post by mat14 on 2016-12-20
Result:

```
sudo gdisk -l /dev/sdb
[sudo] password di mat: 
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 117210240 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 45CE2398-1EDA-4388-9E04-AF3B216A320A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117210206
Partitions will be aligned on 2048-sector boundaries
Total free space is 117210173 sectors (55.9 GiB)

```

---

### Post by oldfred on 2016-12-20
This says it is a 60GB drive.
[https://www.amazon.com/Fujitsu-MHT2060AT-60GB-4200RPM-Drive/dp/B0000ATDBK](https://www.amazon.com/Fujitsu-MHT2060AT-60GB-4200RPM-Drive/dp/B0000ATDBK)

Is 2TB drive something Else?

---

### Post by mat14 on 2016-12-20
Well, in the first printout I posted, testdisk DID find a 2 TB partition. But it is not recoverable. Or did the MFT fool testdisk making it believe there was a 2 TB partition but there isn't?

---

### Post by oldfred on 2016-12-20
You are not going to get a 2TB partition on a 60GB drive.
I think there is some confusion on which drive is which or what you actually purchased, or what was shipped.

What does this show?
 sudo lshw -C Disk -short  

And does BIOS/UEFI have same info?

---

### Post by mat14 on 2016-12-21
Hm. Could be a bogus drive... but testdisk nevertheless states that even  in its opinion it should be 2 tb. I'll check into the matter again  after the holidays (open the drive and look at the model number).
Thank You for now and 
Buon natale   <<-

---

