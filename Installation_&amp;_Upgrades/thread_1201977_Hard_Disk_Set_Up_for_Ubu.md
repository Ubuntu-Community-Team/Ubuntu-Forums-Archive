---
title: "Hard Disk Set Up for Ubu"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by will190780 on 2009-07-01
Hello,

I'm looking to split a 160gb drive into 3. One for Ubuntu one for XP and one for experimentation. From reading around I'm thinking of:=

Swap  2GB (Same as Ram)
/boot   0.5GB
/        15gb Ubuntu (Main operating system)
?        15gb Mint or other Linux (Can't figure what this would be mounted as)
Fat32 50GB (Later formatted into NTFS for Windows)
/home Rest of space

Have I misinderstood this or am I trying too much? Should I just accept that I need to stump up for more HD space? I also have a NTFS 300GB that I was wanting to keep all my downloads and personal files on.

Help would be much appreciated as I need to do something sharpish because my mouse stopped working (software issue) and I figure a new install will fix.

Thanks in advance

Will

---

### Post by oldfred on 2009-07-01
There are more partitioning schemes than hard drives made and most are not "wrong".  One moderator suggested separate /home for each Linux but a /data (like your 300GB drive) for any data to be shared in various copies of Linux. I like a shared FAT32 partition for any data I share between Windows and Linux since I boot both. I have my Firefox and Thunderbird files on the FAT32 partition so I can read my mail in any system I boot. If you are not sure you also can keep some space unallocated for future use. 
It is easier to install Windows first and then install Linux. Windows likes to be first and will overwrite the MBR. SuperGrub will allow you to fix it but it is still easier to do Windows first.

---

### Post by will190780 on 2009-07-02
Hey thanks for the help. In that case I will proceed with a format and install through Windows then throw Ubuntu on.

What mount point would you recommend using for my second Linux system partition?

---

