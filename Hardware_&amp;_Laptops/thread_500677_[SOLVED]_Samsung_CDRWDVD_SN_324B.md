---
title: "[SOLVED] Samsung CDRW/DVD_SN_324B"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by popch on 2007-07-14
Installing Feisty (7.04) on a Dell Optiplex sx260  using a Samsung CDRW/DVD_SN_324B fails: boots fine, loads kernel, then shows message 'can't access tty; Job control turned off', finally stands still at prompt (initramfs)_.  Presumable cause of problem: CD works and can be booted from but is not properly supported by ubuntu any more.

Installing Ubuntu Linux 6.10 using the very same hardware works flawlessly. Updating from 6.10 to 7.04 via internet also works.

But: after updating from 6.10 to 7.04, the device will not recognize any media. However, it can be seen in the device manager as a scsi device with the name CDRW/DVD SN-324B.

---

### Post by jhoward23 on 2007-08-05
I am experiencing the same issue w/ the same drive.  Cross-referencing thread:

[http://ubuntuforums.org/showthread.php?p=3137229](http://ubuntuforums.org/showthread.php?p=3137229)

---

### Post by popch on 2007-08-06
Tody, I received the following PM:

> Actually, I think I found out what the problem was/is. Feisty uses a kernel (2.6.20) that uses libata for PATA devices (which would include our CD-RW drive), and support was spotty. I think they either fixed it in subsequent kernels or reverted to whatever was there prior to the advent of libata. I tried installing the Alpha-3 version of Gutsy and it booted just fine, as did Edgy. So I think it's just an issue with Feisty.

---

