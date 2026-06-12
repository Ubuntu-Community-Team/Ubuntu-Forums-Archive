---
title: "What are all these partitions?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by funky_uncle on 2009-04-26
When I installed Ibex I made a separate partition for /home since I plan to dual boot with other linux distros. So I assumed I would have one partition for / and one for /home. But in GParted, my harddisk looks like this:[IMG]http://img164.imageshack.us/img164/2087/screenshot1k.png[/IMG]
I assume the partition called "linux-swap" is a swap partition Ubuntu created automatically. I have no idea what the "extended" one is.

When I install a second distro, I should shrink the /home partition to make room for a new one, right?

---

### Post by RuleMaker on 2009-04-26
Swap partitions are used by linux as "virtual" RAM memory. Extended partition is just a container for logical partitions.

---

### Post by sgosnell on 2009-04-26
If you look closely at the gparted partition graphic, you'll see that the swap partition is inside the extended partition.  It's a logical partition inside the primary paritition.  I wouldn't do anything about them, and wouldn't worry about them.  You need a swap partition in most cases, and the new OS should use it automatically.  I wouldn't shrink the /home partition, I would keep things as they are.  On second thought, if you want to dual-boot the new distro along with what you have now, there will have to be some partition changes, but the installer should take care of that for you.

---

### Post by funky_uncle on 2009-04-27
So an *extended* partition is a part of the disk that is *"physically"* set aside from the other, and this extende partition can contain one or more *logical* partitions. Am I right?

What are the rules for what names the partitions get? I see / is called sda1, /home is called sda3, the extended partition is sda2, and the logical partition inside it is sda5. What happened to sda4?

Will the partitions have the same names regardless of what distro I look at them from? If I boot OpenSUSE, will sda1 still be called sda1?

---

### Post by dubref on 2009-04-27
sda4 is set aside for 4th primary partition. There can be max of 4 primary partitions (but many logical partitions in your extended partition) Extended partition counts as one primary partition. (This 4 partition limit applies if your hard drive uses MBR to store partition information, which 99% of drives still do).

You should be able to use same /home from different distributions. In my case I am using same /home for different Ubuntu versions(8.10,9.04 each has / in different partition and use /home in yet another partition). I usually do not let installations manage my partitions and do it manually with Gparted(from liveCD)

Incidentally, you can put Ubuntu(and most other distributions, Fedora definitely) in extended partitions, however Windows XP(in case ever need arises) lives best in a primary partition.

---

### Post by funky_uncle on 2009-05-01
Thanks.

But I hear there are potential problems with a separate /home partition, namely that it may cause conflicts between programs on the different distros (like if one distro has Firefox 2 and the other has Firefox 3 and they're both using the same directories to store settings etc).

So I figured I should just let each distro have its own /home. But when I install a new distro, it seems to use the separate /home partition automatically. And I obviously can't just delete /home. But maybe I could just move it back under /? If you know what I mean.

---

