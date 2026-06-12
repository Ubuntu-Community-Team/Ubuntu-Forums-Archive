---
title: "Hardware recomendation in 2018? amd vs intel etc?"
date: 2018-07-03
forum: Hardware
---

### Post by robehickman on 2018-07-03
Hi,

My current system is beginning to become problematic due mainly to a lack of sata ports (4) and no available pcie slots, thus It looks like I'm going to have to upgrade it in the near future. What are peoples experiences with AMD (ryzen) vs Intel these days? This is my main development workstation which is normally on 100% of the time and must be stable. I've seen some indications on here and elsewhere of stability issues on AMD, some indicating it being related to C6 power states.

My main requirements for this is that it must have at least 6 sata ports and more would be highly desirable. I also do not want any lighting of any of any description, and the RGB craze is a big turn off for me. I don't need my computer emulating a fairground attraction. What motherboards have you had good/bad experiences with?

---

### Post by TheFu on 2018-07-03
I've been planning to replace some 10 yr old systems with a single cheap-ish home-built upgrade.  I plan to spend less than $450 total, which would get a solid CPU, MB and 16G of RAM. 

More SATA ports is useful, but there are $90 cards that provide 8 more ports from reputable vendors, LSI.  They have 2 SAS controllers and each SAS can split into 4 SATA ports.

As for CPU and motherboards, if you want stability and few surprises, then avoid anything less than a year old. This applies to every MB + CPU maker.

If you don't hibernate or suspend, then the power states just don't matter.  I never hibernate due to security.  I suspend only 1 laptop, but never any other systems.

I run virtual machines so for my needs, more cores is more important than faster cores. That means AMD has the current advantage on value.  Also, I care about power use and heating, so the CPU will be a 65W version, not a 95W version.

If you mainly run single threaded applications, then Intel has the advantage for performance.  I've run both AMD and Intel CPUs over the decades.  Intel has more of the recent security problems. than AMD, but both have issues which will need 3+ yrs to be solved.

Right now, DDR4 RAM prices are the main problem for me.   AMD CPUs are a great deal right now.  The 1600 and 1700 versions fit well in my requirements.  There are X370 motherboards with 8+ SATA ports with good reputations.  But DDR4 RAM on the approved RAM list are still $170+. Last time I bought 16G of RAM, it was $56.

So, I'd start on *pcpartpicker* looking at the CPUs, then MBs, then compatible RAM. Remember, to stay with 1+yr old parts to avoid early adopter problems on Linux.  That really is too bad, because the newer Ryzen 2600g and 2400g would solve another issue - they include an on-board GPU, unlike the 1600/1700 CPUs.   But I want to avoid problems more than I want "new".   **New is the enemy of stable.**

[https://www.pcworld.com/article/3175005/computers/amd-ryzen-motherboards-explained-the-crucial-differences-in-every-am4-chipset.html](https://www.pcworld.com/article/3175005/computers/amd-ryzen-motherboards-explained-the-crucial-differences-in-every-am4-chipset.html) Explains the differences in the 4 different lines of Ryzen motherboards.

And the good thing about AMD motherboards and CPUs is they don't come out with a different CPU socket every year forcing a new MB every time you want a new CPU, which is part of Intel's business model. 

But this is just 1 person's opinion.  Hopefully, some others will chime in with theirs.

---

### Post by robehickman on 2018-07-03
Hi TheFu

> 
More SATA ports is useful, but there are $90 cards that provide 8 more  ports from reputable vendors, LSI.  They have 2 SAS controllers and each  SAS can split into 4 SATA ports.


I am aware of this option, but I'd be looking for something that is just a HBA, not a hardware RAID controller, and reputable ones such as LSI seem hard to come by and expensive in the UK. I don't see why a device which just adds ports would be more expensive than most high end motherboards. It seems that file systems like ZFS and BTRFS are superior to traditional RAID as the checksums gives the filesystem more information about what is in error.

--

I agree that RAM prices suck at the moment, and have also come to the conclusion that AMD offers better value especially with the extended time period they support sockets for. GPU isn't a problem as I already have a rx560 which is fine for what I need.

---

### Post by TheFu on 2018-07-03
The LSI controllers aren't RAID. They are just JBOD - Amazon sells them.  They are recommended by the FreeNAS guys.

ZFS might be a great solution for data storage.  I wouldn't use it for the OS or boot. I need to migration my media storage to ZFS. I've used ZFS, but only on Solaris.

I wouldn't touch BTRFS. Redhat deprecating it didn't help. Plus it makes tools like  du/df liars.

---

### Post by robehickman on 2018-07-03
You mean this one?

[https://www.amazon.co.uk/LSI-SAS-9207-8i-8-Port-6Gbps/dp/B00AENN2L2/ref=sr_1_4?s=computers&ie=UTF8&qid=1530639139&sr=1-4&keywords=lsi+hba](https://www.amazon.co.uk/LSI-SAS-9207-8i-8-Port-6Gbps/dp/B00AENN2L2/ref=sr_1_4?s=computers&ie=UTF8&qid=1530639139&sr=1-4&keywords=lsi+hba)

Slightly cheaper option manufactured by a different brand but apparently using an LSI chipset:

[https://www.amazon.co.uk/10Gtek-Internal-Express-Controller-SAS2008/dp/B01M2AC40Y/ref=sr_1_2?ie=UTF8&qid=1530638835&sr=8-2&keywords=lsi+hba](https://www.amazon.co.uk/10Gtek-Internal-Express-Controller-SAS2008/dp/B01M2AC40Y/ref=sr_1_2?ie=UTF8&qid=1530638835&sr=8-2&keywords=lsi+hba)

These always seem to be around £120 to £200 here.

> 
I wouldn't touch BTRFS. Redhat deprecating it didn't help. Plus it makes tools like  du/df liars.


Thanks for the heads up.

The OS boots from an SSD, then I have another hard drive which is used as a scratch-pad, and a pair of large drives which store a number of git repository and a lot of image files in a system I designed, which borrows from git but is centralised like svn. I want to mirror these but currently an undecided on how, traditional raid seems to have questionable effectiveness now and ZFS uses a lot of memory. I'm somewhat leaning towards just having one as a primary and using rsync to update the secondary drive.

---

### Post by TheFu on 2018-07-04
Nothing replaces having backups. Definitely not RAID.

I don't remember exact LSI models.  They are recommended in the FreeNAS forums. BSD is pickier about hardware than Linux. You can also check the Linux HCL for disk HBAs, but usually if BSD and ZFS are supported, Linux support is there too.
 
ZFS uses a bunch of RAM only if you use advanced features like deduplication. If you don't use those, it isn't bad.

---

### Post by robehickman on 2018-07-04
I am aware of that and also have a copy of this stored encrypted on glacier via s3.

In that case ZFS may work. Deduplication would not be useful for me as shttpfs (my binary file manager) already does whole file deduplication. I don't believe getting any more granular than that with image and video files is useful. This data set is primarily added to and rarely changes in place. Plus image compression tends to cause cascading changes in a file when they are only slightly changed. Storage is also cheap these days.

---

### Post by kurt18947 on 2018-07-04
The Ryzen APUs (integrated video) seems to have a pretty serious video issue on kernels lower than about 4.16 or 4.17. There may be a split screen video image or a system may not boot. Using a separate video card until the problem is sorted seems to work.

[https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/1032693-ryzen-2200g-still-not-reliable-in-4-18rc2-when-will-it-work](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/1032693-ryzen-2200g-still-not-reliable-in-4-18rc2-when-will-it-work)

---

### Post by robehickman on 2018-07-05
@kurt18947

Thanks for pointing that out, it would be useful information to others reading this.

--

Random thought that is somewhat off topic:

One thing that I'm unsure about with ZFS and similar file systems is that their snapshotting feature is essentially a weak version control system, however as far as I am aware this history data is essentially locked to the drive or drive pool with no easy way to move it off, critically onto other 'standard' file systems, a feature which git and similar have no issue with as they live at level higher in the stack. Even centralised systems don't have that problem as their backing store is just a bunch of regular files.

The biggest complaint I have with traditional filesystems is the inability to get a consistent view as of a given point in time. This causes issues with file synchronisers and VCS systems as the data can change while the system is working, causing it to get a false view of reality and tie itself in a knot. ZFS could solve that problem, however snapshotting would have to be used in a very deliberate way, used purely to get an atomic view then discarded. Using this in combination with another 'user level' version control system, given they are both tracking history, could produce some weird results.

---

