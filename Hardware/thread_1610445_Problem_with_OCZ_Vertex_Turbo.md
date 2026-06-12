---
title: "Problem with OCZ Vertex Turbo"
date: 2010-10-31
forum: Hardware
---

### Post by paddy2706 on 2010-10-31
I just got a OCZ Vertex Turbo SSD from our IT Department for testing purposes.
I inserted it into a lenovo T61 and tried to Install Ubuntu 10.10 (64-bit variant), from the Standard Install CD on it. It does recognize the harddrive, but it throws me tons of errors and Installations fails at formatting/partitioning the drive

I have posted a few lines out of the syslog that refer to that issue (the keep repeating itself thousands of times): [http://ubuntu.pastebin.com/yg4x1ED7](http://ubuntu.pastebin.com/yg4x1ED7)

Is there a known problem with that device? Do I need to follow any special steps in Order to use the drive? It installed "Windows 7" in my colleague's test before without any problems.

---

### Post by efflandt on 2010-10-31
Doesn't OCZ provide a program to do a clean erase and/or to test it?  I could not find anything on OCZ's website like that, but there is apparently a program you can get if you do 10 posts to their forum [http://www.ocztechnologyforum.com/forum/showthread.php?57874-Clean-wipe-of-Vertex-SSD](http://www.ocztechnologyforum.com/forum/showthread.php?57874-Clean-wipe-of-Vertex-SSD)

I got an 80 GB Intel X25-M and Intel has a program for download to test or secure erase their own devices, and I believe it also can run short or long generic tests on other drives.  I used a 4 year old Toshiba laptop to install 64-bit Maverick on it without any issues.  For sudo hdparm -t I got 120 GB/sec the SSD (limited by SATA I) vs. 31 MB/sec for its slow 4200 RAM hard drive.  On my desktop w/SATA II, the SSD reads 250 MB/sec vs. 117 MB/sec for Seagate 7200 RPM drive.

I think I read somewhere that an SSD drive is erased by writing all ones to it instead of all zeros, but I could be wrong about that.

---

