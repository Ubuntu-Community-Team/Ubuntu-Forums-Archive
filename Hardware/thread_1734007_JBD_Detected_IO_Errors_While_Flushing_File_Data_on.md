---
title: "JBD: Detected IO Errors While Flushing File Data on sda1"
date: 2011-04-19
forum: Hardware
---

### Post by kerryhall on 2011-04-19
Got this error while trying to install 10.04.2 alternate.

Is there some sort of hard drive diagnostic tool bundled with the installer, like the CD and RAM diagnostic tools? If not, why not? If so, how do I access it?

Is it possible this is a bug and not a failing hard drive?

Thanks!

---

### Post by psusi on 2011-04-19
System -> Administration -> Disk Utility

Check the SMART statistics.  Make sure the attributes for pending, reallocated, and offline_uncorrectable are 0, and run the long self test.

---

### Post by kerryhall on 2011-04-20
Sorry, I meant from the alternate installer. I can't use the regular installer, as my computer doesn't have enough RAM to run Metacity. 

Thanks!

---

### Post by psusi on 2011-04-20
What is this, a 10 year old computer with less than 256 mb of ram?  If so then it sounds like the hard drive is failing.

---

### Post by kerryhall on 2011-04-22
Yes, it is an old machine, and my guess too is the hard drive is failing. It would just be nice if the alternate installer had hard drive diagnostic tools built it. Where can I suggest this idea?

Thanks!

---

### Post by kerryhall on 2011-04-22
Ok, I threw the HD in a machine that can run Metacity. I ran the disk utility, and it says SMART is not supported on that drive, despite the fact that it is: 

[www.seagate.com/support/disc/ata/st32122a.html](www.seagate.com/support/disc/ata/st32122a.html) 

(says so in the manual)

---

