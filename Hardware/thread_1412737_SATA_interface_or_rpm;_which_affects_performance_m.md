---
title: "SATA interface or rpm; which affects performance more?"
date: 2010-02-21
forum: Hardware
---

### Post by nair on 2010-02-21
This is just a generic computer hardware question unrelated to Ubuntu. This seemed like the best sub forum for the question. Which of the following types of hard drives would you generally expect to have higher performance, ie. faster read/write speeds?
 
(1) a SATA I WD Raptor, 10000 rpm, or
 
(2) a SATA II laptop hard drive, 5400 rpm.
 
Obviously 10000 rpm has been the high performance standard for platter hard drives for years, but the 5 year old one I have available is only SATA I. Didn't know if a cheap SATA II laptop hard drive replacement, which I also have available, would offer higher performance. Sorry if this is the wrong sub forum for my question.

---

### Post by kidders on 2010-02-22
Hi there,

That's a tough question to answer. In general, increasing a drive's rpm affects different aspects of performance than the move from SATA I to SATA II does. A lot also depends on how your disks would be used (eg RAID array, mail server, and so on). For example, using a higher platter rotation speed should give you a small seek time bump, while using SATA II's higher data rate should result in marginally better burst speeds. In your specific situation, one or other (or neither!) may be significant. Further, the differences may be small enough that something as simple as your choice of filesystem could erode them entirely.

In a typical, general purpose environment, my guess (for what it's worth) is that any performance difference would be negligible. In other words, in a situation where your disk wouldn't be heavily loaded with a specific type of I/O operation, I doubt there'd be much between them in practice. Rather than focusing on the platters & the I/O interfaces, I'd be more interested in their capacities, on-board buffer sizes, power consumption & noisiness.

Sorry if that doesn't help much help. Your question is very general.

---

