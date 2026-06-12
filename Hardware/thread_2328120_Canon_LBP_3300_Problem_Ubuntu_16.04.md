---
title: "Canon LBP 3300 Problem Ubuntu 16.04"
date: 2016-06-17
forum: Hardware
---

### Post by tareq.mhd on 2016-06-17
I am using Canon LBP3300 printer which is not working on Ubuntu 16.04. I need to make it workable so that I can use Ubuntu all the time. Thanks in advance.

Update: I have installed the CAPT driver, Ubuntu recognizes it as printer but it can not print after providing print command.

---

### Post by tareq.mhd on 2016-06-21
bump

---

### Post by DuckHook on 2016-06-21
> **tareq.mhd said:**
> I am using Canon LBP3300 printer which is not working on Ubuntu 16.04. I need to make it workable so that I can use Ubuntu all the time. Thanks in advance.

Update: I have installed the CAPT driver, Ubuntu recognizes it as printer but it can not print after providing print command.I do not own a Canon printer so can only point you in the rough direction for a solution, but have you looked at this following AU thread? [http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04](http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04)

This assumes that you are using the 64-bit architecture. If you are already on 32-bit then you don't need to use *add-architecture*. However, just because the Canon driver has a 64-bit version, this doesn't mean that you can forego the *add-architecture* step because, apparently, the binary blobs in the driver are still 32-bit.

Slightly off topic but worth mentioning for general users who happen on this thread: I find that some printer manufacturers are problematic with Ubuntu and Linux in general. My best experience is with HP followed by Samsung. It goes downhill very fast after that. Canon and Brother are popular printers in the Windows world, but not that well supported in the Linux world. If you have a choice between purchasing different brands, this is an important consideration.

---

