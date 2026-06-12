---
title: "Seagate disk read error/anomaly"
date: 2020-07-01
forum: Hardware
---

### Post by ereagle33 on 2020-07-01
Here's a strange situation. I know that the conventional wisdom is ***'backup now... buy a new disk soon'*** but my instinct tells me there is something else afoot. I'm just trying to understand what's happening a little better and have plenty of time for problem solving these days. Besides, I haven't heard great things about the newer Seagate SMR technology in use these days, plus there's the whole HDD vs SSD decision to make...

This may be too long to read for many, but I hope the rest of you find it interesting/challenging... as I do, but I have a vested interest.

The basic options are:


[LIST=1]
[*]The disk really is failing. (Based on the work documented below, I'm not so sure, but am open to the idea.)
[*]There is problem elsewhere in the system: OS, power, bad cable, RAM, etc.
[*]There was some transient (i.e. gremlin) at the time that caused the anomaly and the disk is otherwise fine after the repair, at least until the next transient.
[*]<Insert your favorite option here>
[/LIST]

For those of you willing to read further, here's the setup:


[LIST=1]
[*]The machine in question runs Ubuntu 18.04 with the latest updates. It is an HTPC (Intel Atom, Nvidia ION, MythTV) and runs 24/7.
[*] The disk in question (Seagate Momentus ST9500325AS, 500GB, 2.5 inch, 5400 rpm, 8MB cache) is my main media drive,  running **24/7 since 2010**. Other than daily recordings, there are multiple backups of the media files, so no worry there.
[*]Boot drive is a separate Crucial M4 SSD, so no worry there either.
[*]System is on a UPS.
[/LIST]

Here's the sequence of events so far


[LIST=1]
[*]One day, a program recorded (i.e. write to disk) successfully using MythTV, ending at 10:30.
[*]MythTV attempted to read the file to mark commercials for skipping, and encountered read errors. I tried to play the file and received read errors.
[*]syslog contained the following
```

Jun  7 10:30:13 aeh-htpc kernel: [330264.232823] print_req_error: I/O error, dev sda, sector 171079680
Jun  7 10:30:15 aeh-htpc kernel: [330266.635824] print_req_error: I/O error, dev sda, sector 171079680
Jun  7 10:31:39 aeh-htpc kernel: [330350.552658] print_req_error: I/O error, dev sda, sector 171079680
Jun  7 10:46:17 aeh-htpc smartd[670]: Device: /dev/sda [SAT], 1 Currently unreadable (pending) sectors
Jun  7 10:46:18 aeh-htpc smartd[670]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Jun  7 11:16:17 aeh-htpc smartd[670]: Device: /dev/sda [SAT], 1 Currently unreadable (pending) sectors
Jun  7 11:16:17 aeh-htpc smartd[670]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Jun  7 11:46:17 aeh-htpc smartd[670]: Device: /dev/sda [SAT], 1 Currently unreadable (pending) sectors
Jun  7 11:46:17 aeh-htpc smartd[670]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors

```
[*]dmesg contained the following
```
[609750.100525] ata1.00: exception Emask 0x0 SAct 0x40000000 SErr 0x0 action 0x0
[609750.100537] ata1.00: irq_stat 0x40000008
[609750.100545] ata1.00: failed command: READ FPDMA QUEUED
[609750.100559] ata1.00: cmd 60/08:f0:00:78:32/00:00:0a:00:00/40 tag 30 ncq dma 4096 in
                         res 41/40:08:00:78:32/00:00:0a:00:00/00 Emask 0x409 (media error) <F>
[609750.100676] ata1.00: status: { DRDY ERR }
[609750.100683] ata1.00: error: { UNC }
[609750.137946] ata1.00: configured for UDMA/133
[609750.137986] sd 0:0:0:0: [sda] tag#30 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[609750.137994] sd 0:0:0:0: [sda] tag#30 Sense Key : Medium Error [current]
[609750.138000] sd 0:0:0:0: [sda] tag#30 Add. Sense: Unrecovered read error - auto reallocate failed
[609750.138008] sd 0:0:0:0: [sda] tag#30 CDB: Read(10) 28 00 0a 32 78 00 00 00 08 00
[609750.138012] print_req_error: I/O error, dev sda, sector 171079680
[609750.138086] ata1: EH complete


```
[*]I ran **badblocks** to find all the bad blocks on the disk. There were 271 blocks reported as bad, mostly somewhat sequential.
[*]I used **debugfs **to find that all the bad blocks were marked as in-use.
[*]I used **debugfs** to find the inode number for each of the blocks
[*]I used **debugfs** to find that there were all associated with the media file in question, i.e. no other part of the disk reported errors.
[*]I used **hdparm --write-sector** to write each of the bad sectors. This completed successfully.
[*]I renamed the file to *.bad_blocks_never_delete* as a wait-and-see experiment.
[*]I have run multiple **dd if=.bad... of=.bad... conv=notrunc** commands to read and re-write the same blocks over and over again. I received no errors.  By "no errors" I mean no reported errors in syslog/dmesg or at the command line.
[*]I have received no errors during normal recording/processing/playing operations over the next few weeks.
[*]The output of **smartctl** does change over time, but it isn't clear to me that it indicates disk failure. smartctl output is cryptic and somewhat vendor specific. Even though there are no new errors reported, the fields that have changed values are: Raw_Read_Error_Rate, Seek_Error_Rate, and Hardware_ECC_Recovered. I've attached the latest for your perusal.
[*]As a next step, I am considering deleting the file to free up the "bad" (but now corrected) block to see what happens.
[/LIST]

Thoughts?

Thanks for your interest.

---

### Post by Autodave on 2020-07-01
Realize that a good HD test (same with a RAM test) does not necessarily mean that there are no problems: it just means that the problem didn't manifest itself while the test was underway.

It sounds to me like the HD is going south.

---

### Post by deadflowr on 2020-07-01
You have over 3000 [s]uncorrectable sector count[/s] reported uncorrectable errors reported.
Disks is in bad shape.

Edied: oops I meant reported uncorrectable errors instead of uncorrectable sector count.

But there has got to be  a reason the status number is 187 for it though.

---

### Post by crip720 on 2020-07-01
You have backups so look around for deals on a new hard drive.  When the old drive dies, put the new one in.  For a ten year old drive, can probably get a bigger SSD for less than paid for the old one.

---

### Post by ereagle33 on 2020-07-01
deadflowr - Thanks for the thoughts.

Just FYI, immediately after the failure and before I "fixed" the "uncorrected read" errors, this count was 97 if I recall, so (most of) those errors are associated with the uncorrected read errors that seems to have been corrected by the write-sectors... I imagine that repeated attempts to read and different block sizes could account for most of this large number... I'll keep my eye on this number.

I know I had (unknown) errors long ago when I plugged in the SATA data cable but not the power cable... duh... so not all "errors" are created equal.

---

### Post by ereagle33 on 2020-07-01
crip720 - True... I have 1GB in my shopping cart, waiting for checkout for less than I paid for the original. I also got to read up on the latest SMR vs CMR debate.

Unfortunately, I come from the "if it ain't broke, don't fix it" and the "if it is broke, try to fix it" camp. (I spent hours yesterday taking apart a 20+ year old vacuum because the power cord on the auto rewind spool had a torn cover in places. It was fun, dirty, I learned some stuff and I saved a few bucks.)

In this case, I'm just trying to understand a little more about how the system works and how to interpret the things smart reports and figure out why "can't read" seems to be fixed by "write", at least for now.

---

### Post by TheFu on 2020-07-01
i had a similar problem with a Plex OS + DB + media HDD a few weeks ago.  This was the 2nd disk in that slot with issues the last 6 yrs.  i have backup religion, but the hassles and worry of an inconvenient failure putting that server off line (and destroying the WAF) have me replace it with a WD data center drive w/ 5 yr warranty and 4.5M hr MTBF rating.

The old disk is still around and working (last time i checked), so perhaps i'll run some badblocks destructive write tests over an eSATA connection just for fun. That won't be soon.  Another disk in a RAiD1 array has been warning about failure the last few days, so that will take priority next maintenance window. 

SMART doesn't show any problems about 22% of the time and a disk still fails.

---

### Post by ereagle33 on 2020-07-02
One note of update - some Seagate drive is inhererently incorrect in the default smartctl command output. Apparently they encode both error counts and total numbers in the same value. The following command line will properly show that the listed fields (i.e. Raw_Read_Error_Rate, Seek_Error_Rate, and Hardware_ECC_Recovered) are in fact without error.
```
smartctl -a -v 1,raw48:54 -v 7,raw48:54 -v 195,raw48:54 /dev/sda
```
So I quess, it is just the **Reported_Uncorrect** field that troubles me. In this case it seems that it could not correct them while reading, but did correct them with subsequent write, so I think I can rationalize not panicing at this point.

---

### Post by ereagle33 on 2020-07-05
One final update: Well, I finally took the plunge and deleted the file containing the bad blocks. I used **debugfs** to confirm that the blocks were indeed free. I then made a copy of a 30GB backup file without error. I again used debugfs to confirm that the blocks were allocated to the new file. I then made a copy of the copy (i.e. read the bad blocks) without error. I then deleted the two copies and confirmed with **smartctl** that there were no new disk errors.

Bottom line is that although I cannot determine why the blocks became unreadable and I cannot determine why they were not automatically reallocated by the drive and/or the filesystem, I have not seen any additional errors on that disk, so I'm sticking with it.

Hopefully, this will encourage someone else to investigate apparent disk failures a little more closely before pulling the trigger on a new disk, depending on the situation of course.

Thanks for the feedback.

---

### Post by kurt18947 on 2020-07-05
I've read to not install an SSD in a video or surveillance system. Those systems perform lots of writes, far more than what general use PCs do. Writes wear SSDs much more than conventional hard drives and video systems don't really benefit from the additional speed of SSDs. As to your current drive, it's run nonstop for about 10 years. I'd say it's due for an honorable retirement.

---

