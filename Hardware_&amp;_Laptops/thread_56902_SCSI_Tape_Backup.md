---
title: "SCSI Tape Backup"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by guy_uk on 2005-08-14
Hi Again folks

further to my reply in the SIIG scsi card post; i've done some digging.

Please bear with me - newbie...

What i'm trying to achieve is to backup directories from home directory to tape, on a daily schedule.

I've got an HP surestore 24i drive (DDS3) connected to a SCSI PCI card (iWill)

After some digging, i've got SCSI packages from the repositories and i can now do various things to the tape drive such as get status info and eject/rewind the tape etc

I can't however write to the drive (using tar - example below) but the tapes i am using have been formatted by either backup exec or yosemite tapeware - do i need to reformat them before tar can write to the tapes? if so, how do i do that?

output :-
> **root@newserver:/home/guy # mt -f /dev/st0 status**
drive type = Generic SCSI-2 tape
drive status = 620756992
sense key error = 0
residue count = 0
file number = 0
block number = 0
Tape block size 0 bytes. Density code 0x25 (unknown).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN
**root@newserver:/home/guy # tar cvf /dev/st0 guytest**
guytest/
guytest/test.txt
guytest/test.txt~
tar: /dev/st0: Warning: Cannot close: Input/output error
**root@newserver:/home/guy #**


there's plenty of tape info via google, but it seems focussed on 'ftape' and those floppy-bus tape drives - which i find is inappropriate.

If i do format a tape, what file system?  :-? 

can anyone help me? am i going in the right direction?

Thanks in advance, Guy

---

### Post by nad on 2005-08-15
As these are used tapes, the first thing I would do is erase and retension (now that you know how to issue commands and move the tape).

There is no "filesystem" on tape. It is just a stream of data created by an application. If your tape is not positioned correctly when you issue a write command, the existing data is simply overwritten and you will possibly have an eof mark beyond your new one without a beginning record.

The point being that there is no formatting necessary to use the tapes. Tapes do wear out however. It would be prudent to purchase new tapes once you are certain that the backup method works.

---

### Post by guy_uk on 2005-08-15
thanks for the reply Nad

Sweet, i read man mt and erased/retentioned the tape as you suggested and i was able to succesfully write a test folder to the tape, and read the contents back afterwards

 :grin: 

i suppose i should have tried that before but i was worried i might render the tape useless if it needed a filesystem.

Tapes have only seen 2 hours or so use. I hope to try a genuine data backup later on this evening.

I do have 4(edit!) other questions if anyone could help relating to linux backup good practice ...?  

naturally i want to squeeze as much data onto the tape as possible, i was wondering would i see any gains in for example bzip'ing the directories first and then tar'ing them onto the tape?

from my understanding the hp surestore 24i supports 'hardware compression',
can i take advantage of this somehow?

can i still use my cleaning cartridges in linux?

Finally, regarding restoring data, am i better off streaming a directory structure onto the tape - e.g. if there is a read error i may lose 1 file out of 1000 instead of the whole 1000 in 1 damaged bzip(or similar) file?

thanks for your time

Guy

---

### Post by rich257 on 2006-01-14
Here's what I had to do to get a SCSI tape drive working with Breezy 5.10.

I needed to install the **mt-st** module and then edit **/etc/stinit.def** to add the configuration for the drive.  Read the comments at the top of the file for where to find examples.  You can find the drive manufacturer and model from looking in **/proc/scsi/scsi**.  Then I did
```
dkpg-reconfigure mt-st
```
and it reported that 1 tape drive was initialised.

Following that you should be able to use **mt** to check the status of the drive.

---

### Post by Kadin2048 on 2006-03-24
I had similar issues and eventually I just ended up guessing, and it seems to work ... no guarantees that it'll do anything for anyone else, though.

In my /etc/stinit.def file I added the following -- this is for my HP SureStore Tape 12000e, which is a DDS-2 autoloader:

# A compressing DAT (DDS-1-DC or DDS-[234])
# Inserted for HP SureStoreTape 12000c
manufacturer=HP model = "C1553A" {
can-bsr can-partitions auto-lock
mode1 blocksize=0 compression=1
mode2 blocksize=1024 compression=1
mode3 blocksize=0 compression=0
mode4 blocksize=1024 compression=0 }

I just ripped this from the examples and inserted the manufacturer and model of my drive, as reported by cat /proc/scsi/scsi .

---

### Post by towerofsong on 2006-04-11
I have a DAT24 HP Surestore mode number "C1537A" which I am trying to get working with Ubuntu. I have installed mt-st and it appears in /proc/scsi/scsi OK. I have entered 
manufacturer=HP model = "C1537A" {
can-bsr can-partitions auto-lock
mode1 blocksize=0 compression=1
mode2 blocksize=1024 compression=1
mode3 blocksize=0 compression=0
mode4 blocksize=1024 compression=0 }

into /etc/stinit.def but when i run mt-st dpkg-reconfigure it says "initialized 0 tape devices"

Any ideas?
Cheers

---

### Post by towerofsong on 2006-04-11
I have sorted something out, I did modprobe st and i can now see the tape with mt -f /dev/st0 status
although mt-st dpkg-reconfigure still doesn't work properly
hmmm
I'll test it and see if I can backup to the tape now.

---

