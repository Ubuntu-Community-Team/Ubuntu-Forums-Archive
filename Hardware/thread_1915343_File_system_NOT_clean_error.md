---
title: "File system NOT clean error"
date: 2012-01-26
forum: Hardware
---

### Post by Usksider on 2012-01-26
Hi everyone,

I have a dual boot laptop running Windows 7 and Ubuntu 11.10. The internal hard disk has 3 main partitions: 1 for Windows, 1 for Linux and 1 that I call New Volume for files I transfer between the two operating systems (mostly music and images). I also have a 1TB USB drive attached.

I installed a bunch of updates to Ubuntu 11.10 yesterday and this morning I can't write to my USB drive or to partition used for storing/swapping files; both mount as read only. In an effort to sort the problem I used Disk Utility to unmount the New Volume partition and checking the file system I get a message saying "file system NOT clean". Clicking the check and repair file system button again just crashes Disk Utility and I have no idea what to do to rectify the situation. Can anyone help?

I should add: I can read and write as normal when running Windows. :confused:

---

### Post by Usksider on 2012-01-26
I may have found a work-around....

Okay, being desperate to get at some files and not wanting to resort to Windoze I just used Synaptic to install NTSF-3G and un-install NTSF Progs. This has given me read/write access to my drives, BUT although they seem to be working properly the New Volume and USB drive still report "file system NOT clean" in Disk Utility.

---

