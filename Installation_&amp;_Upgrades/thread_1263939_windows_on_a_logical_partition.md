---
title: "windows on a logical partition"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by BackwardsDown on 2009-09-11
Hi!

I installed Windows 7 which deleted all my Logical partitions. With a recovery program I have all my partitions back but the windows 7 is not a primary partition anymore.

As I don't want to reinstall Windows 7 again, is there a way to make the NTFS primary? Or is there a way to let Windows 7 boot off a logical partition?

[IMG]http://img11.imageshack.us/img11/5191/schermafdrukm.png[/IMG]

Many thanks!

---

### Post by louieb on 2009-09-11
99% sure you won't get windows to boot when its in a logical partition. 

[TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")  should be able to change the partition to a primary one. Which recovery program did you use? 

sfdisk or fdisk can do it but I'm no expert on either one. I've used sfdisk on a test PC to change partitions from logical to primary - but in that case it did not matter if screwed up beyond repair - don'f feel qualfied to give advise on how to use it.  [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

### Post by BackwardsDown on 2009-09-11
I used TestDisk to recover my lost partitions.

I think I'll backup all my files and then fiddle with testdisk and fdisk later this week, as I understand it is possible.

---

### Post by louieb on 2009-09-11
Good news - testdisk  can redo the partition as a primary boot able one. Then a [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") should be able to boot it. Just depends on how your partitions got messed up to begin with. This guy did a similar thing  [http://ubuntuforums.org/showthread.php?t=1261173](http://ubuntuforums.org/showthread.php?t=1261173) - long thread -  testdisk shows up in post #17.

---

### Post by Bartender on 2009-09-11
I'm curious - how did you manage to turn the Windows primaryu into an extended??

---

### Post by BackwardsDown on 2009-09-12
> Just depends on how your partitions got messed up to begin with.

I can read all my files on all my partitions so I think its OK.

> **Bartender said:**
> I'm curious - how did you manage to turn the Windows primaryu into an extended??

Windows 7 deleted all my logic partitions. After recovering my logical partitions testDisk put all the partitions in 1 extended partition, so they are all logical now.

---

### Post by BackwardsDown on 2009-09-13
Got the job done with testdisk.

Thanks!

---

