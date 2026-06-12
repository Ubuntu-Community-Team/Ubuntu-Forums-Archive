---
title: "Boasted copying speed illusion problem - Ubuntu 14.04LTS Mate 1.8.1"
date: 2015-03-18
forum: Hardware
---

### Post by Muhammad_Ahmad_Mujtaba on 2015-03-18
Hi, I am Ahmad.

I am using Ubuntu 14.04LTS on my Lenovo B570e machine. I am facing an issue regarding copying data to USB drives.

i) Data from USB to machine works fine, I get speed on the average of 20MB/s which is fine to me.
ii) Data from machine to USB stick does not work quite right, On the start of copying it shows 10x of actual speed and gradually it decreases to the level in KB/s which takes quite a good amount of time. I copy different things mostly in .iso format (Installation images, games repacks and so on) to my other Windows based machine.
How can I resolve this issue, It is quite troubling:

My machine is:
Lenovo B570e
Intel Core i3-2330M 2.2 Ghz x64
RAM 4GB HD 500GB
Intel HD 3000

and USB Stick is:
Kingston DT 101 4GB FAT32
Sandisk USB 16GB NTFS/FAT32

OS is:
Ubuntu 14.04LTS Mate 1.8.1

I'm attaching some snaps below.

[http://pho.to/93mYe](http://pho.to/93mYe)

---

### Post by coldraven on 2015-03-18
FAT32 has a 4GB file size limit. Are you trying to copy .iso files bigger than that?

From Wikipedia: [https://en.wikipedia.org/wiki/Fat32#FAT32](https://en.wikipedia.org/wiki/Fat32#FAT32)
> The maximum possible size for a file on a FAT32 volume is 4 GiB minus 1 byte or 4,294,967,295 (2[SUP]32[/SUP] &#8722; 1)  bytes. This limit is a consequence of the file length entry in the  directory table and would also affect huge FAT16 partitions with a  sufficient sector size.[SUP][[1]]("https://en.wikipedia.org/wiki/Fat32#cite_note-GB4-1")[/SUP] Large video files, DVD images, and databases easily exceed this limit.

---

### Post by tgalati4 on 2015-03-18
That's normal behavior.  Typically the file copy is sent to RAM (which is fast) and gives misleading transfer speeds, but then the file actually gets written to the USB which is quite slow.  As I recall, the USB writing algorithm does some bundling of data blocks before being sent to the USB storage device.  This reduces wear and improves the already slow performnce.

If you pull the USB stick too fast because you think it is finished writing, then you will have a corrupt USB.  You have to wait a long, long time for the USB to be finished.  Sometimes you can use the hard disk activity light as a clue.  Sometimes you will get an error:  "Device in Use" when you try to eject.  That is something you should respect because the data is not finished being sent to the USB.

Some report that writing to USB sticks is much faster in Windows--that's possible.  Windows will load a different driver for each USB, as provided by the manufacturer, and that could result in much faster writes.  Linux uses a universal USB module and that makes it the lowest common denominator as far as performance is concerned.

If you are writing large files to USB sticks, use a stopwatch to see how long it really takes and calculate your own throughput.  Use that as a guide for large writes in the future.  Relying on the dialog box estimate will get you in trouble.  It is merely a suggestion.

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-03-19
> **coldraven said:**
> FAT32 has a 4GB file size limit. Are you trying to copy .iso files bigger than that?

From Wikipedia: [https://en.wikipedia.org/wiki/Fat32#FAT32](https://en.wikipedia.org/wiki/Fat32#FAT32)

Yes, I already know this and use NTFS for more than 4GB of data.

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-03-19
> **tgalati4 said:**
> That's normal behavior.
This is not so good, I copy/move data quite a lot and it becomes a headache to wait w/o the end of operation. I feel this is wrong. Not technically but yes visually. A native Windows user might get negative impression from Linux/Ubuntu and may revert back to Windows again. Any hope of solution to the problem in future?


> If you are writing large files to USB sticks, use a stopwatch to see how long it really takes and calculate your own throughput.  Use that as a guide for large writes in the future.  Relying on the dialog box estimate will get you in trouble.  It is merely a suggestion.

That's a good suggestion and can there possibile an app or software which shows read write rate over specific drive so that it may serve as notion for whether process of copying/moving is on going or ending OR any process in system monitnor app which can be peeked upon through out copying? Something like that?
Plus, I have read copying speed varies on the style of data being copied i.e. one large file say largeFile.iso [4GB] will have different copy speed than pictures and videos collection of 4GB. In such a case, stopwatch idea may not be so good.

---

### Post by tgalati4 on 2015-03-19
You can format your USB sticks to ext2, ext3 or ext4 and get better transfer results.  Writing to NTFS will be slower because it is going through a file system translation.

Yes, there are performance issues in Linux for certain workloads and certain Use Cases.  I don't use Windows anymore so I am not bothered by such performance comparisons.  

You can install *iostat* (part of the *sysstat* package) and monitor throughput speeds to a very fine detail.  Let us know what you find.

```
sudo apt-get install sysstat
man iostat
iostat

```

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-03-20
IOSTAT is a nice thing, a technical one. I hope this would help me from now and on.

> Linux 3.13.0-37-generic (ahmad-Lenovo-B570e) 	20/03/15 	_x86_64_	(4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          12.57    0.04    2.64    1.80    0.00   82.95


Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              14.63       150.23       221.05    1840237    2707636


These are outcomes from the iostat command. 
Thanks for the help. . .

---

