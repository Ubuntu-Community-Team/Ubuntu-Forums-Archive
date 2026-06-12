---
title: "partitioning pen drive?"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by sitric on 2007-02-19
hey i have a 2 GB USB 2.0 pen drive...
is it possible to partition the pen drive to have multiple volumes...
i want to put DSL on a 100Mb partition and want to keep the rest for data carrying purposes...
making folders just doesnt do the job....
plz help...

---

### Post by DagMan on 2007-02-19
I've found that windows can have trouble recognising more than one partition and if your first partition is the bootable one, then perhaps windows would only see that on, assuming it was formatted in a fat filesystem.  Having a linux filesystem on the first partition and a fat partition on the second was what did not work for me and windows saw nothing, however I did not try it with both filesystems using FAT.

But yes, you can generally format the usbsticks.  They can be a pain to get right because they tend to want to mount as soon as a new filesystem is created and should be unmounted for the operation but after lots of playing around they've always gone fine for me.

With a stick that size, you can fit a Knoppix on it. [http://www.google.com.au/search?hl=en&q=knoppix+on+a+usb+stick&btnG=Google+Search&meta=](http://www.google.com.au/search?hl=en&q=knoppix+on+a+usb+stick&btnG=Google+Search&meta=)

---

