---
title: "care and feeding of a hard drive"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by halfmanhalfbug on 2007-09-06
Chao Ubuntus
The hard drive in my laptop melted down. How best to check/maintain the new drive?
-Is linux hard on hard drives? I had several lockups when the "three finger salute" (ctl-alt-backspce) did not work so I had to use the power button. Is there a better way to handle this situation?
-when partitioning the new drive I had to use the Windows installer because GParted would not deal with a windows partition that had one or more bad blocks. I ran fsck -c on the linux partition and it looks OK (no bad blocks listed). I understand it is too late to use badblocks because the drive is already formatted. True? What's the best way to handle a new drive? Badblocks then partition then fsck?
-Is "fsck -c" OK to run on a mounted drive? (with the -c option it's read-only)
-What's the best way to clone the drive in case this happens again? rsync?
-What are good and bad drives? The one that failed was a 2-year-old Hitachi Travelstar.
-can a small ant crawl into the "airhole" on a drive? Can anything get in? (not such a stupid question here in Vietnam)
Thanks for any help!
hmhb

---

### Post by Claus7 on 2007-09-06
Hello,

it's very sad that your hard drive melted down. I hope that you kept back up and you didn't lose valuable data.
May I won't answer to most of your questions, yet this is what I did to an external HDD:
[http://ubuntuforums.org/showthread.php?t=435870](http://ubuntuforums.org/showthread.php?t=435870)
The idea about a new internal drive I think is the same.

As far as good and bad drives is concerned I think that apart from the brand and the characteristics, unfortunately you never know. So keeping backups to a cd is not a bad idea.

Regards!

---

### Post by halfmanhalfbug on 2007-09-07
Thanks Claus7. I had a backup of my home directory so it wasn't so bad :)
Your description of partitioning was also very helpful
Thanks again,
hmhb

---

