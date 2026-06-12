---
title: "Is this hard drive dead?"
date: 2009-03-15
forum: Hardware
---

### Post by Volt9000 on 2009-03-15
Initially while installing Ubuntu I had big problems. I finally traced the problem to (what appears to be) a bad hard drive.

Once I got Ubuntu up and running I was hoping to resolve any issues I had with this hard drive by virginizing it. I tried using dd to write zeros all over the hard drive, and here's what I got:

> 
ubuntu@ubuntu:/dev$ sudo dd if=/dev/zero of=/dev/sdb bs=512
dd: writing `/dev/sdb': Input/output error
90481+0 records in
90480+0 records out
46325760 bytes (46 MB) copied, 32.0482 s, 1.4 MB/s 


I also got some warning about SMART when I ran the diagnostics utility for this drive in Windows.
Does this mean the hard drive is gone?

---

### Post by jpeddicord on 2009-03-15
> **Volt9000 said:**
> I also got some warning about SMART when I ran the diagnostics utility for this drive in Windows.
Does this mean the hard drive is gone?

SMART errors usually mean that unfortunately the drive may be dying. I had a drive that constantly spat out self-test SMART errors and it was because the drive's motor wasn't working right. It had to be replaced.

---

### Post by miegiel on 2009-03-15
Every harddisk manufacturer has a disk diagnose utillity you can download from their site. Westerndigital has 3, for example, dos floppy, dos cd (both bootable I assume) and a windows executable.

---

### Post by Volt9000 on 2009-03-15
Thanks for your help guys.

> **jacobmp92 said:**
> SMART errors usually mean that unfortunately the drive may be dying. I had a drive that constantly spat out self-test SMART errors and it was because the drive's motor wasn't working right. It had to be replaced.
Crap, I was afraid of that. :(
The thing that bothers me is that this hard drive worked perfectly fine up until the last time I used it, which was about a year ago. The hard drive has been sitting aside on my desk ever since, never been used, and now all of a sudden it's no good. :(

> **miegiel said:**
> Every harddisk manufacturer has a disk diagnose utillity you can download from their site. Westerndigital has 3, for example, dos floppy, dos cd (both bootable I assume) and a windows executable.
Yes, I ran WD Diagnostics on it and that's how I found out about the SMART errors.

---

