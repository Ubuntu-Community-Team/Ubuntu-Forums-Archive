---
title: "hard drive failure with raid"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by andrewwk on 2007-08-16
Greetings all,

Here is the background of the server I'm running:

Intel D6965WH motherboard
Core 2 Duo
2048 RAM
3ware 9650se-4LPML
4 Seagate 80 Gb hard drives

Here is my problem.  I am running Ubuntu 7.04 on a raid 10.  I put this server together in July 2007 and since then, I've had four drive failures.  I thought the first 2 failures were hardware failures, but yesterday, 2 failures within 15 minutes of each other.  One of the drives that failed was just installed the day before.  I did a hardware check on the 2 drives that failed and found out there was nothing physically wrong with them.  I erased the two drives and put them back in the server, rebuilt the array, and are working fine.  Any ideas what is wrong?

Thanks,
WK

---

### Post by andrewwk on 2007-08-28
I found out that the errors happened when the hard drive times out.  I talked to 3ware and the engineer told me to disable queuing.  The server has run for over a week with out a melt down.

---

