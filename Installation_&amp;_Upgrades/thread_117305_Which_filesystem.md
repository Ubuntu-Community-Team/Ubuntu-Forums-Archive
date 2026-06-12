---
title: "Which filesystem?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by rjpa on 2006-01-14
Hi,

I'm about to install Ubuntu 5.10 on my laptop, but now I'm about to conider which filesystem I want on it: JFS, XFS, EXT2, ReiserFS or EXT3.

I have considered these options:

> /dev/hda1 SWAP 1GB
/dev/hda2 Ext2 /boot 512MB
/dev/hda3 ReiserFS / 20GB
/dev/hda4 Ext3 /home 70GB

Is this considered a good choice?

My laptop is a Asus M6N Centrino 1.6GHz, 512Mb RAM, 100GB 5400RPM ATA100 Disk and ATI 9600 M10 Mobility.

Please help me in my choice of correctly choice of filesystems and layout.

- rjpa

---

### Post by matthew on 2006-01-14
What you describe should be fine. 

My feeling is that unless you have specific, special requirements most of them will serve you well with no noticable difference. I would tend to recommend ext2/3 just because they are so common. 

If you really want to look into the differences and do some further research [this page is likely to interest you]("http://en.wikipedia.org/wiki/Comparison_of_file_systems"). Otherwise, set it up as you describe and it should turn out well.

---

