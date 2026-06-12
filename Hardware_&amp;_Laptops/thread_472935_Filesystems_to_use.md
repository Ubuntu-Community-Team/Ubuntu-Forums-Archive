---
title: "Filesystems to use?"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by happysmileman on 2007-06-13
I'm getting (hopefully) an e3xternal hard drive and would like to know what filesystems to use per partition...

I intend to have a Linux From Scratch partition, and maybe some partitions for Distros I don't have the room for, or don't want to replace current distro with on main drive...

I figure all the Linux systems will use ext3 (probably, all the ones I've tried so far have) but I want to know what filesystem to be used for the rest, which will be a partition just for random files such as music to save space on HDD...

I've heard a lot of people say FAT32 is the way top go since it can be read by windows and Linux, however it apparently starts to get slow after about 10GBs... And I may have upwards of 100GBs left over after installing some distros so this would probably have horrible performance (especially on an external drive)...

Can anyone suggest any better filesystems, they don't necessarily have to be readable by Windows, though obviously it's an extra feature and I have Windows, I don't use it but brother does and he might want to take advantage of my free space

---

### Post by HotShotDJ on 2007-06-13
For just random files, I prefer ReisersFS -- However, if you use EXT3, there are drivers that you can install in Windows so that it can be read, and quite frankly, on a USB drive I'm not sure that there would be much of a performance difference between ReisersFS and EXT3.

Just my personal opinions.  Your mileage may vary.

---

### Post by happysmileman on 2007-06-13
Reiser or Ext3... Which is better performance-wise, especially on large or external drives?

---

### Post by ahaslam on 2007-06-13
I use ext2 on my usb drive (fast & has windows drivers should relatives want anything). Be aware that fat systems don't differentiate between case, recognise permissions or allow large files.

---

### Post by happysmileman on 2007-06-13
> **ahaslam said:**
> I use ext2 on my usb drive (fast & has windows drivers should relatives want anything). Be aware that fat systems don't differentiate between case, recognise permissions or allow large files.

Well the 4GB limit wouldn't really bother me, but yeah I don't want FAT, and my brother probably wouldn't mind using Linux to move files since he seems to use it a bit anyway...

I just want speed and efficiency on Linux mainly... Is ext3 just a better version of ext2 or are there advantages to each, and how do they compare to Reiser

---

### Post by ahaslam on 2007-06-13
Ext3 is a journalled version of ext2, hence it's noticeably slower.

PS. Performance is really found with XFS & JFS, I've never used the later as I'm satisfied with XFS.

---

### Post by happysmileman on 2007-06-14
Ok I think i'll use ext2 (assuming I get the money for the hard-drive) unless anyone can give me a reason not to

---

### Post by ahaslam on 2007-06-15
Good choice ;)

---

### Post by stonesbg on 2007-11-07
Hi I have recently switched from windows to Linux (Ubuntu).  I use linux as a server for hosting files and streaming video.  I have recently had a problem with getting a corruption on a hard drive and am wondering if this is just a cuase of using NTFS and if so would it be better to switch to a filesystem that would be better paired with Ubuntu.  I would need a filesystem that is reliable and has fast access speed  for large files both read and right as this will be used for in samba.

Any advice and help will be much appreciated

---

