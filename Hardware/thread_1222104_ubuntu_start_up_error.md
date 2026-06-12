---
title: "ubuntu start up error"
date: 2009-07-24
forum: Hardware
---

### Post by gallaharsha on 2009-07-24
Hi,

I have ubuntu startup problems. I get the first screen which shows various IDE Channels etc. and cursor blinks at the bottom of the screen after the line: Boot from CD:

Everything was working great until today. Somebody help me out as I need to get back to work as early as possible.

Thanks in advance.

---

### Post by cariboo on 2009-07-24
Change the boot order in the BIOS, so that it boots from the first hard drive.

---

### Post by philcamlin on 2009-07-24
> **cariboo907 said:**
> change the boot order in the bios, so that it boots from the first hard drive.
+1

---

### Post by gallaharsha on 2009-07-24
Hi,

After restarting several times, it worked fine, then to check i restarted it again and this time grub loaded and when i selected the ubuntu then it threw out errors which look something like this..

ata 6.0: revalidation failed(errno=5)
end_request: i/o error on device sdb,sector 0
buffer i/o error on device sdb, logical block 0

...many lines which look similar to the above.


Thanks in advance.

---

