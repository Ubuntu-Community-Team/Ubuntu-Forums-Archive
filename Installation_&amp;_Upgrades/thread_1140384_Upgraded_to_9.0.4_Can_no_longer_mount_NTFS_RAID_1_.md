---
title: "Upgraded to 9.0.4 Can no longer mount NTFS RAID 1 with dmraid"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Spazghost on 2009-04-27
Hello,

Prior to upgrading today, I was running 8.10 64 bit.

I have an NTFS formatted Raid 1 which I use for storing my data.
I used to be able to easily access it in ubuntu by just doing:```
sudo dmraid -ay
mount -f ntfs /dev/mapper/blah /mnt/raid
```

However I am having difficulty doing this in 9.0.4... The volumes show as active in dmraid when I run dmraid -ay, however they do not show when I open up computer, and when I attempt to mount the raid device using the exact same syntax I had used in 8.10, it fails and gives me the syntax text for the mount command...

I don't know what I'm doing wrong but I'm somewhat frustrated as I am no unable to access all of my data from my linux partition.

---

