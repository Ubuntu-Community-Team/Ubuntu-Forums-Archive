---
title: "Multiboot question"
date: 2008-08-05
forum: General Help
---

### Post by And6ate9 on 2008-08-05
I just want to some clearification on what I have read to make sure I am on the right path. Now I have a 500gb drive partitioned into 4 section 1. xp 2. ubuntu 3. swap. 4 NTFS unused.

I read that the windows only allows for 4 partitions or primary partitions? Then it is also possible to take on of those partitions have like as many sub partitions as you want readable by only unix like OSes? 

Is that about right? So it's possible for my to use my 4 partition for instaling other distros and ubuntu or grub can detect thos partitions?

---

### Post by And6ate9 on 2008-08-05
I just want to some clearification on what I have read to make sure I am on the right path. Now I have a 500gb drive partitioned into 4 section 1. xp 2. ubuntu 3. swap. 4 NTFS unused.

I read that the windows only allows for 4 partitions or primary partitions? Then it is also possible to take on of those partitions have like as many sub partitions as you want readable by only unix like OSes? 

Is that about right? So it's possible for my to use my 4 partition for instaling other distros and ubuntu or grub can detect thos partitions?

---

### Post by spiderbatdad on 2008-08-05
linux allows the use of an extended partition, which is a primary partition that can be divided up into more than 4 partitions. How many? I don't know...more than 8.:)

---

### Post by TomSharp on 2008-08-05
This might not be what you are looking to do, but if you format your fourth partition as EXT3 (what Ubuntu uses) rather than NTFS, I don't think Windows will see it anyway, so you can split it into as many primary or logical partitions as you want.
Tom

---

### Post by bodhi.zazen on 2008-08-05
Yes, easily :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

Also: Please do not start multiple duplicate threads, causes confusion and duplication of effort :)

---

