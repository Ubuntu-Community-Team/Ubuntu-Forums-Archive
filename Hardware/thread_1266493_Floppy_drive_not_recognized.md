---
title: "Floppy drive not recognized"
date: 2009-09-14
forum: Hardware
---

### Post by jheis on 2009-09-14
I've installed 9.04 on an old Thinkpad with a floppy drive mainly so that I can transfer some old files from floppies to a USB flash drive so that I can transfer them to my T43.

The problem is that Jaunty doesn't seem to "see" the built in floppy drive. Is there some secret handshake I'm missing?

James

---

### Post by x22 on 2009-09-18
a floppy drive would be /dev/fd0; have you tried
something like "mount /dev/fd0"?

oh yes, another thing: the disk must have a file
system supported by your kernel.

---

### Post by chuckbb on 2009-09-25
Same Problem Here. Cannot mount drive, regardless of all the other threads found on this forum. I'm Using Jauntry 9.04. As a noob, i'm looking for a step by step, easy to follow procedure to mount that drive. 

Cya,

Chuck

---

### Post by and003 on 2010-08-21
> **chuckbb said:**
> Same Problem Here. Cannot mount drive, regardless of all the other threads found on this forum. I'm Using Jauntry 9.04. As a noob, i'm looking for a step by step, easy to follow procedure to mount that drive.
A step-by-step solution can be found here:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

---

