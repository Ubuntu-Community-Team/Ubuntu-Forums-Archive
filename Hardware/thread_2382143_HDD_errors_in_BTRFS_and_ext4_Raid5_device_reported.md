---
title: "HDD errors in BTRFS and ext4 Raid5: device reported invalid CHS sector 0"
date: 2018-01-09
forum: Hardware
---

### Post by sandman852 on 2018-01-09
Hey guys!

I am about to install a new Home Server with Ubuntu 16.04 LTS with an updated Kernel to 4.14.12. The Hardware is as follows:
[LIST]
[*]Pentium G4600 CPU
[*]ASRock H270M-ITX/ac Mainboard
[*]2x4GB Ram
[*]OCZ Vertex 2 SSD for System
[*]3x6TB HDD (Seagate Ironwolf, ST6000VN0033)
[/LIST]

The reason for upgrading to Kernel 4.14 was because I had the plan to use BTRFS with its built-in Raid5 functions on the HDDs [-o<
Unfortunately I am already experiencing some errors with one of the HDDs. I tried to copy some data to the Raid and after a few hundreds of MBs, the speed was going down to almost 0 KB/s and the file transfer was cancelled. In syslog I was able to find the following:
[https://paste.ubuntu.com/26355282/](https://paste.ubuntu.com/26355282/)

After that, I made a "wipefs -a" on all the 3 HDDs and recreated the BTRFS Raid Array --> Same behavior and errors.
My next step was to change the SATA Cable --> Same behavior and errors.
Further step to switch the ports, and again I recreated the BTRFS Array:
- ata2 -> ata3
- ata3 -> ata4
- ata4 -> ata2
==> Errors moved from ata2 to ata3:
[https://paste.ubuntu.com/26355334/](https://paste.ubuntu.com/26355334/)

My next attempt was to create a software based Raid5 using madam with ext4 partition. The setup went absolutely smoothly and also the syncing of the discs was without any errors (took about 10 hrs). Sadly, my first copying of files to the newly created Raid produced pretty much the same errors again, but not as much:
[https://paste.ubuntu.com/26355380/](https://paste.ubuntu.com/26355380/)

Do you have any idea what could be wrong? I am still no 100% convinced it really is the HDD as it is brand new... 
I did do a long SMART test on the three HDDs with the following results:
sdb: [https://paste.ubuntu.com/26355421/](https://paste.ubuntu.com/26355421/)
sbc: [https://paste.ubuntu.com/26355433/](https://paste.ubuntu.com/26355433/)
sdd:[https://paste.ubuntu.com/26355426/](https://paste.ubuntu.com/26355426/)

Do you have any advise on how I could proceed? 
Thanks a lot in advance!

Greetings
Sandman

---

### Post by TheFu on 2018-01-10
Looking at the SMART data.
* One of the drives (ST6000VN0033-2EE110) has a VERY HIGH relocated sector count. It is failing.  Replace it immediately.  Preferably with a non-Seagate disk!!! Seagate has a poor reputation for spinning disk since around 2006-ish.  You might want to look up the Backblaze disk failure quarterly report for alternative vendor selections.
* Both of the other disks are showing very high read error rates, which is usually related to a bad cable, but can be failing disk controller.  IMHO, all the data is suspect that goes through so much read errors.

Regardless, backup your data immediately and replace that disk with all the relocated sectors.  I consider any count of relocated sectors over 10 to be "replace immediately".  Then I might keep using the disk for trivial "sneaker-net" stuff, if at all.

---

### Post by sandman852 on 2018-01-10
@TheFu: Thanks for your comments!
I will return the disks to my retailer. I already got in touch with him, but they will be replaced with exactly the same models. When the parcel service originally delivered them to me, the packaging was in a very bad condition. Maybe that's why the disks are also in a very bad condition. Because, actually they are brand new...
Fortunately I do not yet have any other than test data on the drives, so there's nothing to be backed up :grin:

Btw.: Initially I was explicitly choosing these drives, because they are specified with an URE of 1*10^15 and not 1*10^14 as the WD drives are and therefore they have a significantly lower chance of having an URE during the rebuild of the Raid5 array. I noticed that e.g. Backblaze is using almost nothing else than drives with an URE of 1*10^14. So it seems that this number may be not as significant, as I expect it to be, right?

Greetings, 
Sandman

---

### Post by TheFu on 2018-01-10
I have ZERO idea what you mean by URE.  

I just know that Seagate has a poor life expectancy compared to most other brands of spinning HDDs.  I've been burned a number of times since 2007 or so.  Actually had a party when the last seagate disk died.  I've had other vendor disks fail, but not nearly as close to the end of warranty as with the seagates.  That company will never get another dime from me.  This is sad because I was very loyal to them previously.  I actually have some 320G Seagates here, still spinning, in an array.  They are 12 yrs old with ZERO relocated sectors and none have caused any issues.  Spinning 24/7/365 all this time.

Clearly, other disks have failed over the years too.  But those had reasonable warranties (5 yrs) and I felt like the value was good when they finally did fail.  Once in a while, we all get a bad disk too.  I've had that from all the vendors, including seagate.  That's just life. I don't hold it against them.  

BTW, the 2 disks that don't have any relocated sectors - I think those are probably fine. The disk controller they are connected with or the cables is where I'd look for problems.

But my tiny sample of disks isn't statically relevant to make any real decisions.  Look at large vendors, see what they see.  Why is it that none of the disk makers share their failure rates?  Something to hide?

---

