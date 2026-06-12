---
title: "first time fsck - understanding what it means"
date: 2020-12-13
forum: Hardware
---

### Post by crackers_altitude on 2020-12-13
I would like to understand what to expect from my system, as it seems the drive all of a sudden had about 20 errors that needed fsck.ext4 to repair. Apparently, it is all back to normal now, as I can boot up and everything seems fine. All I'm hoping to hear are broad ideas to consider as this system continues aging. I am happy that fsck worked - as I thought it usually mean the end. Maybe it still does.

A brief story:

One day, a system I have ( see details below) froze up, and a reboot brought up a "busybox" and "initfsram" console output. It seemed the 1-year old drive I had might need fsck, although the rescue DVD reported the drive file system did not have errors. This was the first time I ever had to run fsck, so I followed the instructions from initfsram and used fsck.ext4 with the appropriate options, and simply reported "y" to everything. there were about 20 things that needed fixing - I did not keep track. Booted back up from the drive, and everything seems fine.

Some points that I think might partly explain the development of the drive errors :

* size of solid state drive vs. "tera bytes written" (TBW) - I chose a small-ish (500 GB) drive, however, this might have been a lower TBW, and therefore, more likely to develop errors.
* location of drive in machine - perhaps insufficient cooling (see details) compared to a..  non-solid-state drive - especially since the drive is "underneath" the optical drive, and the OD had been running for a long time at the time the system froze. 

Thanks for any comments, including how to write about this topic.

details:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal
Linux baobab 5.4.0-56-generic #62-Ubuntu SMP Mon Nov 23 19:20:19 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
 
storage : 

ATA Samsung SSD 860 - 500 GB, 

this drive is controlled by an ASMedia ASM 1062 serial ATA controller. it is a very unusual connection by USB. It worked fine for a year. This could be contributing to the apparent problem. It is so strange I can't precisely recall how it is working without thinking about it more.

cpu : AMD Athlon(tm) 7450 Dual-Core Processor

Machine : Acer Aspire X1300 - this has the hard drive installed between the optical drive and the motherboard - effectively "underneath" the optical drive.

---

### Post by CatKiller on 2020-12-13
A crash, for any reason, while a drive is in use, will mean that fsck will likely have things to fix. The filesystem has a journal of what was planned to do and what actually got done, so the check will either complete the tasks or roll them back, as appropriate, to put the filesystem in a consistent state.

Having unallocated space is useful for SSDs. The flash cells that store the data have a finite number of times that they can be written to before they can't be written to any more. Having some spares means that the drive controller can more easily do wear-levelling the cells to keep the drive as a whole working for longer.

SSDs run hotter than HDDs, but they also tolerate higher temperatures. Putting the highest performance SSDs right next to high performance GPUs is a common configuration, and is fine.

---

### Post by yancek on 2020-12-13
There are numerous reasons a filesystem may need to be checked with fsck due to some corruption.  fsck simply marks bad blocks it finds so they are not used by the system.  If it begins to happen on a regular basis, it may be a hardware problem.

---

### Post by crackers_altitude on 2020-12-14
I appreciate the help - a couple follow up questions : 

* how is space allocated for spare cells during formatting
* is there a log file somewhere that keeps track of cells that are going bad, or something to that effect?

---

### Post by CatKiller on 2020-12-14
It's all done automagically by the drive controller. It's not something that an OS has access to.

---

### Post by crackers_altitude on 2021-02-15
Never mind.

---

