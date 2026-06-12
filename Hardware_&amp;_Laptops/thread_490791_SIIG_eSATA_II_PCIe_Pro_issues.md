---
title: "SIIG eSATA II PCIe Pro issues"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by shannondoko on 2007-07-02
I have a SIIG eSATA II PCIe Pro card, and it is really flaking out in ubuntu 7.04 (knoppix also)

Is anyone else having this problem? Any solutions? 

<!-- not crucial but might help to understand --> 
My setup is this:
SIIG eSATA card --> WD My Book Premium eSATA 500GB

I got it because I need to copy drive images off a server and USB 2.0 is SLOW! 

Here is the problem
Partitioned/Formated drive ext3 fine
SCP file off server (260GB) gets to maybe 100mb and drive indicator lights stops blinking
yet the progress bar shows that it is still copying(still rather slow over Gigabit crossover) 
I let it finish which took about a day, only to find out that it didn't copy and the drive was giving me I/O errors..
Attempted this multiple times, only paid much closer attention to it, and each time it did the same thing. At first I thought it was the drive, but now I am using USB again, and it is almost done copying with the indicator light and no I/O errors.

---

