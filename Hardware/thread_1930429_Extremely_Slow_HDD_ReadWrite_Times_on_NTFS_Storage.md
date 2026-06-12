---
title: "Extremely Slow HDD Read/Write Times on NTFS Storage Partition"
date: 2012-02-23
forum: Hardware
---

### Post by eternal_sage on 2012-02-23
Hey all. Got a weird error. Have had this setup for months (maybe even over a year... don't remember) and never had any trouble until the last few weeks. I have a 1 TB HDD partitioned up for dual boot, one 30 GB Win7 NTFS partition, one 20 GB Lubuntu 11.10 Ext4 partition, one 4 GB Swap partition, and the rest is a big NTFS partition that I store everything on so I can access from both sides.

For a very long time now, no problems. But recently I can't even open the Storage partition in File Manager without it delaying big time (5 to 10 seconds on average), and manipulating files (editing MP3 tags, for instance) takes upwards of a minute on occasion. Nothing that I know of changed recently, and the other partitions on the same HDD have no issues. Any ideas? I am currently defragging the system from Win7 side to see if this helps, although it reports no fragmentation....

Stupid Windows... if it wasn't for my wife's addiction to Sims 3 I'd just get rid of it....

---

### Post by eternal_sage on 2012-02-23
Also, it seems that there is no issue from the Win7 side. Only Lubuntu having this issue.

---

### Post by eternal_sage on 2012-02-24
Ok, another update. After shutting down to boot to Win7 and then back to Lubuntu everything is more or less ok. It is still slower than it should be, but not even close to the extreme that I was experiencing before. Does NTFS just become unstable after lots of use? And even so, it is still performing less than would be expected.

---

### Post by eternal_sage on 2012-02-24
Okay... nevermind. I figured it out after doing some digging and some thinking. The last time I remembered getting proper performance was before I messed around in fstab trying to get the Storage partition to automount and not be read-only. I also stuck sync in there (for what reason, I honestly couldn't tell you), but after digging around on ntfs-3g I found a little blip about the sync option being extremely slow (which makes sense, I really don't know what I was thinking). I took that option out, rebooted, and have been using the drive doing some heavy mp3 conversion/tag editing/organizing and now the drive is behaving as expected.

In otherwords, don't use sync... especially if you're not sure why you are using it... :D

---

### Post by ahallubuntu on 2012-02-24
Glad you got it figured out.

NTFS has worked great for me in Ubuntu, except for accessing (especially writing) very large files - like 20GB+ image backup files and such.  It's a known problem with the Linux NTFS tools that you get high CPU load and slow access on such files.

If you have concerns about your NTFS file system, run chkdsk in Windows, and also run a defrag once in a while (Windows 7 may have this scheduled automatically).

---

### Post by eternal_sage on 2012-02-24
Thank you! I had noticed that in the ntfs-3g documentation as well, but I appreciate the head's up.

---

