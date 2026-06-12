---
title: "ntfsresize won't"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2009-08-14
Hello,

I have a dual-boot laptop that I rarely boot in Windows. That's why I decided to shrink the Windows partition and give more room to the Linux system.

I booted from SystemRescueCD, tried gparted, and got a message about bad sectors. I have backed up all the partitions in the disk, done several chkdsk /f /r on windows XP, and no errors are found. My conclusion is that the disk may have a few bad sectors, which is not that unusual, but they have been marked and are not in use. The system has always been stable.

Since gparted refuses to touch any disk with bad sectors, I have tried ntfsresize with the --bad-sectors option, directly from the command line. I understand that this option tells ntfsresize that yes, there may be some bad sectors, but we are aware of it, and please go on with your work.

After some successful test runs with the -n parameter, when I try to actually do the job, ntfsresize stalls at about 15%, complains about an input/output error, and quits saying that I should do another chkdsk /f /r.

This is the line I am trying:

```
ntfsresize -f -s 33G /dev/sda1 --bad-sectors 
```

How come ntfsresize finds bad sectors so fast, and Windows doesn't even notice? Is there any way to just skip the bad sectors and get on with it?

---

### Post by Mark Phelps on 2009-08-14
I can't answer the specific question, but you could try using some free MS Windows utilities to resize the partition.  Google for Free Windows Partitioning Utilities and you'll find several of them.  Easus is a good one to use.  See the link below: 

[http://www.partition-tool.com/]("http://www.partition-tool.com/")

---

### Post by AmerNewbieInDE on 2009-08-14
have you tried to boot into windows, then goto adim controls, disk management, select the windows partition, right click, select shrink??

---

### Post by skamarla on 2009-08-14
Right on, Mark!

The Easus tool did a perfect job. I was trying to coerce ntfsresize into doing it, but this was more practical.

AmerNewbieinDE, the native Windows disk admin tool can only do very basic operations. Resizing isn't one of them. Typical.

Thanks a lot.

---

