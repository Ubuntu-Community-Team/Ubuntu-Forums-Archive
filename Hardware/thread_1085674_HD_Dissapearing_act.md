---
title: "HD Dissapearing act"
date: 2009-03-03
forum: Hardware
---

### Post by Walkaloner on 2009-03-03
Hello, I have a PowerSpec Desktop running 3 hard disc drives, one carries Ubuntu, the other is mass storage and the last is Windows XP PRO. After installing Ubuntu, I noticed that I cannot find my mass storage drive (or the Linux hdd) while I am running Windows. however, in ubuntu, i am able to mount, use, and do whatever with any drive. Is there a way to 'release' the drive from ubuntu so i can use this drive in Windows? Thank you for your time! I hope someone can help. -Nick

---

### Post by taurus on 2009-03-03
What filesystem is your mass storage drive?  Windows cannot read ext2/ext3 unless you install fs-driver first.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Walkaloner on 2009-03-05
it is a ntfs drive, and the disc manager in windows says it is (active) , healthy drive. primary partition.i had not used it with ubuntu but to watch a movie from it... that was the only interaction.

---

