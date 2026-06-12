---
title: "Can't mount Western Digital Elements 2TB external hard drive"
date: 2010-09-07
forum: Hardware
---

### Post by ChiVampir on 2010-09-07
I'm trying to mount my new Western Digital Elements 2tb hard drive, but every time I try to plug it into the computer I get this error message: 

> Error mounting: mount exited with exit code 12: Failed to read last sector (3907027119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?I've tried using ntsfix and it seems like it worked:
> chi@reca:~$ sudo ntfsfix /dev/sdb1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.But when I tried opening the hard drive from nautilus I still got the same message as above (no other volumes was connected at the time).

I've also tried opening and watching it in GParted, and I can see it there as a volume that's not allocated. When I tried to allocate the hard it I got the message that it had no partition table. And that I cold make one. I tried and Ubuntu sugested to make a MS-DOS partition table for it. But there I got a little scared as I've not done this before. 

So should I make a MS-DOS partition table, or are there other ways to fix it? 

The external hard drive is brand new and was brought today. And I don't have the possibility to test it with Windows or Mac as I'm using Linux only on my machines. 

Hope someone's able to help :)

---

### Post by ChiVampir on 2010-09-07
I got help on[ LinuxQuestions]("http://linuxquestions.org"):
The problem was solved by giving the hard drive the MS-DOS partition table and formatting it to NTFS, and now it works like a charm :)

---

### Post by colin.p on 2010-09-08
There was a problem with some of the elements drives not properly formatted from the manufacturer. They seemed to work ok in windows, but not in the WDTV Live (which is linux based). WD said to re-format the drives again as NTFS and they would then work. That would be why re-formatting it worked for you running linux.
I have a 2TB drive that worked fine from the manufacturer, but obviously some don't.

---

### Post by ChiVampir on 2010-09-09
Ok, I didn't know that.
Thanks for you answer.

---

### Post by krtica on 2010-09-23
My experience (WD Elements 1.5TB):
Manufacturers format was NTFS with 4096 bytes cluster size.
I had many problems on different comps and OSes.
I recreated a MS-DOS partition table (GParted) and formated it as NTFS with 512 bytes cluster size.
After that, everything worked fine.

---

