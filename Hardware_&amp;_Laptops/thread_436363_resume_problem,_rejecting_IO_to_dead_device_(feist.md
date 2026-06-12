---
title: "resume problem, rejecting I/O to dead device (feisty, thinkpad x31)"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by xenuhn on 2007-05-07
hello,
after hours and hours of searching the web on this problem and trying to get it working, i am now hoping somebody out there will stumble over this thread and has maybe solved it.

suspend seems to work properly, but when i want to resume i got this message continously (sda2 is my root partition):
[ ... ] scsi 0:0:0:0: rejecting I/O to dead device
[ ... ] EXT3-fs error (device sda2): ext3_find_entry: reading directory #<long number> offset 0
[ ... ] scsi 0:0:0:0: rejecting I/O to dead device
[ ... ] EXT3-fs error (device sda2): ext3_find_entry: reading directory #<another long number> offset 0
and so on (<long number> means e.g. 4987324)

so it seems that the kernel lost the "connection" to the harddrive :/
anybody any idea, theory or assumption?

thanks in advance!
xenuhn

---

### Post by poserslipjack on 2007-05-10
Hi Xenuhn,

I am having a very similar issue with my Thinkpad t41p.  I am currently following two bugs on launchpad...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109762](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109762)

...and...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109403](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109403)

Good luck to us both!
-Chris

---

