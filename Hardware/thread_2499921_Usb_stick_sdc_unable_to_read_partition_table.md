---
title: "Usb stick: sdc: unable to read partition table"
date: 2024-08-15
forum: Hardware
---

### Post by maketopsite on 2024-08-15
```
Aug 15 14:21:46 maketopsite kernel: Buffer I/O error on dev sdc, logical block 0, async page read
Aug 15 14:21:46 maketopsite kernel: Buffer I/O error on dev sdc, logical block 0, async page read
Aug 15 14:21:46 maketopsite kernel: I/O error, dev sdc, sector 0 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
Aug 15 14:21:46 maketopsite kernel: Buffer I/O error on dev sdc, logical block 3856368, async page read
Aug 15 14:21:46 maketopsite kernel: I/O error, dev sdc, sector 30850944 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 2
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 01 d6 bf 80 00 00 08 00
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
Aug 15 14:21:46 maketopsite kernel: I/O error, dev sdc, sector 30850944 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 01 d6 bf 80 00 00 08 00
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
Aug 15 14:21:46 maketopsite kernel: sd 6:0:0:0: [sdc] Attached SCSI removable disk
Aug 15 14:21:46 maketopsite kernel:  sdc: unable to read partition table
```

Usb stick is not visible in the output of
```
fdisk -l
```

Does it please mean it's broken beyond repair ?

---

### Post by tea for one on 2024-08-15
The partition table may be damaged?
Is sdc visible with:-
```
sudo parted -l
```

---

### Post by maketopsite on 2024-08-15
> **tea for one said:**
> The partition table may be damaged?
Is sdc visible with:-
```
sudo parted -l
```

```

root@maketopsite:/home/maketopsite # parted -l
Error: /dev/sdc: unrecognised disk label
Model: JetFlash Transcend 16GB (scsi)                                     
Disk /dev/sdc: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
```

---

### Post by tea for one on 2024-08-15
The disk is visible, therefore, why not create a new partition table and a subsequent partition?

---

### Post by yancek on 2024-08-15
What was this device used for?  
Do you know if it had a partition table previously and what it was?
What filesystem type was on the device/partition(s)?

---

### Post by maketopsite on 2024-08-22
> **tea for one said:**
> The disk is visible, therefore, why not create a new partition table and a subsequent partition?

It's low level tool:
```
mkpart [part-type name fs-type] [COLOR=#ff0000]**start**[/COLOR] [COLOR=#ff0000]**end**[/COLOR]
```
I don't want damage something by wrong use of this tool. I would prefer some GUI tools if possible.

---

### Post by maketopsite on 2024-08-22
> **yancek said:**
> What was this device used for?  
Do you know if it had a partition table previously and what it was?
What filesystem type was on the device/partition(s)?

Haiku R4 Beta was installed on this stick on BeFS filesystem. Not sure about previous partition table .

---

### Post by tea for one on 2024-08-22
> **maketopsite said:**
> It's low level tool:
```
mkpart [part-type name fs-type] [COLOR=#ff0000]**start**[/COLOR] [COLOR=#ff0000]**end**[/COLOR]
```
I don't want damage something by wrong use of this tool. I would prefer some GUI tools if possible.
Gparted is available in a "Try Ubuntu" live session

---

### Post by maketopsite on 2024-08-22
> **tea for one said:**
> Gparted is available in a "Try Ubuntu" live session

I'm sorry gparted doesn't see this drive.

---

### Post by tea for one on 2024-08-22
Then try parted via the terminal.
Assuming the disk is still sdc
```
sudo parted /dev/sdc # nominates target disk
```
```
mklabel gpt # create gpt partition table
```
```
quit
```
Open Gparted - Is it recognised?

---

### Post by maketopsite on 2024-08-22
> **tea for one said:**
> Then try parted via the terminal.
Assuming the disk is still sdc
```
sudo parted /dev/sdc # nominates target disk
```
```
mklabel gpt # create gpt partition table
```
```
quit
```
Open Gparted - Is it recognised?

(it's sdb now)
```
root@maketopsite:/home/maketopsite # parted /dev/sdb
GNU Parted 3.5
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt                                                      
Error: Input/output error during read on /dev/sdb
Retry/Ignore/Cancel?   
```

---

### Post by tea for one on 2024-08-22
No progress yet, let's try another method (assuming the target is sdb)
[https://www.rodsbooks.com/gdisk/walkthrough.html](https://www.rodsbooks.com/gdisk/walkthrough.html)
```
sudo gdisk /dev/sdb
``` 
```
v # verify disk
```
```
q # quit
```
Please post output before proceeding

---

### Post by maketopsite on 2024-08-22
> **tea for one said:**
> No progress yet, let's try another method (assuming the target is sdb)
[https://www.rodsbooks.com/gdisk/walkthrough.html](https://www.rodsbooks.com/gdisk/walkthrough.html)
```
sudo gdisk /dev/sdb
``` 
```
v # verify disk
```
```
q # quit
```
Please post output before proceeding

```
root@maketopsite:/home/maketopsite # gdisk /dev/sdb
GPT fdisk (gdisk) version 1.0.9

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): 

```

---

### Post by tea for one on 2024-08-22
Did you not enter the v (verify) command?

---

### Post by maketopsite on 2024-08-22
> **tea for one said:**
> Did you not enter the v (verify) command?

not yet (because of the warning)

```
Command (? for help): v

No problems found. 30851005 free sectors (14.7 GiB) available in 1
segments, the largest of which is 30851005 (14.7 GiB) in size.

Command (? for help): 

```

---

### Post by tea for one on 2024-08-22
I wouldn't worry about warnings right now because we do not know the health status of the device.
Anyway, let's press on
Start gdisk and nominate your usb device.
Try the w command
```
redact@gmktec:~$ sudo gdisk /dev/sdb
[sudo] password for redact: 
GPT fdisk (gdisk) version 1.0.10

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): [COLOR="#0000FF"]w[/COLOR]

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdb.
The operation has completed successfully.
redact@gmktec:~$
```

---

### Post by maketopsite on 2024-08-22
> **tea for one said:**
> I wouldn't worry about warnings right now because we do not know the health status of the device.
Anyway, let's press on
Start gdisk and nominate your usb device.
Try the w command
```
redact@gmktec:~$ sudo gdisk /dev/sdb
[sudo] password for redact: 
GPT fdisk (gdisk) version 1.0.10

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): [COLOR=#0000FF]w[/COLOR]

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdb.
The operation has completed successfully.
redact@gmktec:~$
```

```
Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdb.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

Command (? for help): 

```

---

### Post by tea for one on 2024-08-22
Not looking very hopeful yet.
The advice from gdisk is to use the experts' options.
You reach this sub-menu by selecting [COLOR="#0000FF"]r[/COLOR]

I suggest that you study the gdisk walkthrough, select the [COLOR="#0000FF"]recovery and transformation options[/COLOR] and see if any of the commands can help.
Within gdisk, you always have help at hand by using [COLOR="#0000FF"]? for help[/COLOR]

My gut feeling is that the disk is damaged but, if you are willing to spend more time on this, then I would certainly be interested if a repair were to be successful.

---

### Post by maketopsite on 2024-08-23
> **tea for one said:**
> Not looking very hopeful yet.
The advice from gdisk is to use the experts' options.
You reach this sub-menu by selecting [COLOR=#0000FF]r[/COLOR]

I suggest that you study the gdisk walkthrough, select the [COLOR=#0000FF]recovery and transformation options[/COLOR] and see if any of the commands can help.
Within gdisk, you always have help at hand by using [COLOR=#0000FF]? for help[/COLOR]

My gut feeling is that the disk is damaged but, if you are willing to spend more time on this, then I would certainly be interested if a repair were to be successful.

Thank you. I've tried something but the result is the same.

---

