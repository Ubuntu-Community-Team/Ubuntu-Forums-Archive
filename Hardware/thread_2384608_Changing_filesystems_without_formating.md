---
title: "Changing filesystems without formating?"
date: 2018-02-09
forum: Hardware
---

### Post by a09fc4b1 on 2018-02-09
So not too long ago i installed xubuntu as i often change operating systems and when i installed xubuntu and chose a small 256mb partition of my secondary 150 gb HDD it set the whole disk as swap area  (note, when installing xubuntu it showed as empty which should've been conering now thinking about it). Anyway, is there a way to change it from "linux-swap" format back to "NTFS"  without formating because i have some inportant stuff there, and file recovery isn't mutch of an option because i don't have a disk big enough and i'm broke. The ubuntu  vertion is 16.04 Xenial Xerus

---

### Post by 1clue on 2018-02-09
You did this with the default installer?

If so, then you're probably not going to like the answer. While it's been awhile since I built an ubuntu from scratch, I believe the default is to format partitions it uses.

At any rate, you can go to fdisk (or gdisk for gpt partition tables) and set the filesystem type back to what you think it should be. I'm guessing but I would bet your partitions are gone. It's possible that you could re-create the partition table again if you remember exactly the values you had before, but there may be data missing.

Good luck.

---

### Post by a09fc4b1 on 2018-02-09
Thank you 1clue for your reply! Hopefully ill be able to recover my data. P. S. While installing ( i used try ubuntu) i could easely use and browse the hdd tho i don't think this is of any use.

---

