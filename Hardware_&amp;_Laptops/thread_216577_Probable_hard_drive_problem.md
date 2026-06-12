---
title: "Probable hard drive problem"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by zeace on 2006-07-15
I'm trying to run Ubuntu on a computer I've acquired and I'm getting some error messages when the machine boots from CD:

Buffer I/O error on device dm-1, logical block 3092838

I get about 50 of these, mostly at consecutive blocks.

Which device is dm-1?


The computer is occasionally locking up, and before I acquired it it was a Windoze machine that would sometimes not boot.  They suspected it was a hard drive problem.

Any ideas?

---

### Post by zeace on 2006-07-15
I should add that is during "Starting Enterprise Volume Manager System" and that there are 2 IDE drives in the system

---

### Post by criddled on 2006-08-04
I have the exact same problem when trying to boot from the cd. It hangs at 'Starting Enterprise Volume Manager System' and spits out tons of Buffer i/o errors. I've burned 2 CD's and ensured the md5checksums match. Anyone have a remedy to this problem?

---

### Post by manish.shah.uk on 2006-08-24
I had the exact same problem installing Dapper Drake from CD onto a Windows machine with two IDE hard drives (master and slave). In the end, I disconnected the slave drive from the system and the installation went through ok. I'll tackle adding the drive back another time :)

---

### Post by ROFRSOC on 2006-08-25
I had the same problem too, with the installation hanging on "Starting Enterprise Volume Management System," and spitting out that "buffer I/O error on device dm-1".  At the time I was just trying to preview Ubuntu and not install it.  However, after restarting my system, I found that Windows now ran incredibly slow, and my secondary drive was no longer formatted correctly.  When I attempted to scan it using Partition Magic 8.0, I got a CRC error. The same occured when I tried to check it out using command prompt.    Next, I tried a system restore, which did nothing helpful, and then a repair/reinstall of windows.  This also did nothing, but caused my anti-virus program to stop working.  Of course, at that point I then became infected with quite a few viruses and spyware, and had to get rid of them.  After that, I got a recovery program, recovered the files on my corrupted secondary drive, and formatted it back to NTFS.  As soon as I did that, the slowness problem ceased to exist, which led me to believe that it was due to the corruption of the drive.  So, in a nutshell, I know this may just be a localized problem having to do with possible incompatibility of my hardware to the ubuntu OS, but I do believe it is something that should be looked into.

Regards.

---

