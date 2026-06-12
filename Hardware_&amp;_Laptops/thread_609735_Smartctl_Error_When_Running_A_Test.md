---
title: "Smartctl Error When Running A Test"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by aantn on 2007-11-11
I have experienced no problems with my hard drive. Today, just as a precaution, I tried running:
```
sudo smartctl -t short /dev/sda && sudo smartctl -l selftest /dev/sda
```
It outputs the following:
```
smartctl version 5.37 [powerpc-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Sun Nov 11 17:28:02 2007

Use smartctl -X to abort test.
smartctl version 5.37 [powerpc-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       10%      3828         123590136
# 2  Short offline       Completed: read failure       10%      3825         123590136
# 3  Short offline       Completed: read failure       10%      3825         123590136
# 4  Short offline       Completed: read failure       10%      3825         123590136
# 5  Short offline       Completed: read failure       10%      3825         123590136
# 6  Extended offline    Completed: read failure       10%      3825         123590136
# 7  Extended offline    Completed: read failure       10%      3825         123590136

```

Is this something to worry about?

---

### Post by daradib on 2007-11-12
It could be something to worry about. It could mean the beginning of the end for your hard drive. Right now I get a similar error message as well.
```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       20%      2526         345156222
```

I have a Seagate drive, so I'm going to backup my stuff and then run SeaTools and see what happens.

If anyone can help that would be great.

---

### Post by daradib on 2007-11-12
It could just be a bad sector, so you could try formatting. But first backup your necessary stuff and if you have a Seagate drive, use SeaTools (you can check with your hard drive manufacturer to see if they have a certain tool).

---

### Post by aantn on 2007-11-12
What exactly does seatools do?

Is there any easy way to check the drive manufacturer? The problem is on my internal drive.

---

### Post by daradib on 2007-11-13
> **aantn said:**
> 
Is there any easy way to check the drive manufacturer? The problem is on my internal drive.

System -> Preferences -> Hardware Information
Find your hard drive, and using the Advanced tab, try to determine your manufactuerer.
If you don't know the manufacturer, at least look for a model number, and conduct a Google search for the model number.

> **aantn said:**
> What exactly does seatools do?
[URL="http://www.seagate.com/www/en-us/support/downloads/seatools/"]
[COLOR="Blue"]Seatools[/COLOR][/URL] can test Seagate or Maxtor Parallel ATA (PATA and IDE) and Serial ATA (SATA) interface disc drives. Because the software boots to its own operating system you can test your drive regardless of the OS installed on it.  You can even test a new or completely blank drive.  SeaTools will instruct the drive to run its built in Drive Self Test (DST) and give either a pass or fail status.  If you are troubleshooting your disc drive and the DST passes, then you have a good drive! (Source: [http://www.seagate.com/www/en-us/support/downloads/seatools/](http://www.seagate.com/www/en-us/support/downloads/seatools/))

EDIT: I am refering to SeaTools for DOS, which can be run from a bootable floppy or bootable CD.

---

### Post by daradib on 2007-11-13
BTW, I tried running SeaTools. The Short Test on the drive causing me problems told me to run the Long Test. I ran the long test an it found about 90 bad sectors and claimed it fixed them all. It claimed that my drive *PASSED AFTER REPAIR*. Unfortunately, when I ran the long and short tests again yesterday and today, I got the messages (so apparently nothing was fixed, as I still had 90 bad sectors).

I'm going to determine more information on this and I'll report back. Meanwhile, any help would be appreciated.

Note, according to Seagate:
> Passed after Repair" is a special condition where bad sectors were detected asunreadable and the user gave permission to SeaTools to attempt to reallocate blank replacement sectors which was successful. The drive is now considered a good drive. A few defects are usually not a cause for concern. For example, there are nearly four hundred million sectors on a 200GB drive. Nonetheless, you should run the LONG Test more often to see if there is a trend of growing defects.

And about Long and Short Tests (according to Seagate):
> When you launch the "SHORT Test" most drives will run Drive Self Test. Drive Self Test (DST) is a thorough diagnostic routine that is built in to the hard drive's firmware. Firmware is the
machine language programming the controls the disc drive. DST is completely data safe.

The "SHORT Test" is adequate for most situations. Consider running the "LONG Test" which reads each sector on the drive if you need to run a more comprehensive test.

The "LONG Test" test will take a long time to complete. Because the "LONG Test" reads every sector on the drive, the amount of time required will depend on the speed and capacity of the disc drive. The highest capacity drives often take 2 to 3 hours to complete. At any time, feel free to Cancel the test without harming the drive.

My hard drive is SATA 200 GB, Seagate ST3200826AS.

---

### Post by aantn on 2007-11-14
It seems like its a western digital drive. The only problem is that the recovery tools are only available for dos and windows (I have a Mac).

I bought apple's care plan and I don't think that it has expired yet. I'll see if they can help.

---

### Post by daradib on 2007-11-14
I believe you actually can use Western Digital diagnostic tools (I'm assuming Lifeguard) as long as you can boot from CD/floppy diskette,
> 
The Data Lifeguard Diagnostic Tools are used primarily for determining the physical condition of your hard drive. If you are having computer problems which you suspect are hard drive related, you can test your drive with this tool. This diagnostic utility is designed for hard drives larger than 8.4 GB with the model number starting with WDxxx.

You would use the Lifeguard for DOS, since the downloads are bootable CD and bootable floppy diskette. Just boot into the CD or diskette.
[URL="http://support.wdc.com/download/downloadxml.asp"]
Western Digital Downloads[/URL]

This is what you want. Just burn the ISO and boot from the CD, or use the floppy disk.
[URL="http://support.wdc.com/download/downloadxml.asp#30"]
Data Lifeguard Diagnostics (CD)[/URL]

[Data Lifeguard Diagnostics (Floppy)]("http://support.wdc.com/download/downloadxml.asp#2")

[Knowledgebase Instructions]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1329")

---

### Post by aantn on 2007-11-15
Thanks. I'll try it. Hopefully its architecture independent.

---

### Post by daradib on 2007-11-15
According to Seagate:
> A "Defective drive" can often be revived with a data- destructive zero fill data pattern or a low level format. This is because today's modern disc drives contain thousands of spare sectors which are automatically reallocated if the drive senses difficulty reading or writing. Since SeaTools is read-only (data safe) occasionally a drive with many problem sectors that have not reallocated to a spare sectors can be forced to do so by writing to the sectors. Spare sector reallocation is a normal intelligent drive operation.

Just an update: I tried ran "Zero All" which is a zero fill data-destructive measure that writes zeroes to every sector. Again, the same (about 90) sectors showed up on the screen when I ran the "long test." I also contacted Customer Support (via a web-based form). The reply I received told me to run the "Zero All" again, and that if I still received the same sector errors, then I should submit my drive for warranty.

If anyone has any advice, I would appreciate it.

---

### Post by aantn on 2007-11-15
Thanks for your help.

I'll be away for the weekend, but I'm going to give this a shot when I got back.

---

