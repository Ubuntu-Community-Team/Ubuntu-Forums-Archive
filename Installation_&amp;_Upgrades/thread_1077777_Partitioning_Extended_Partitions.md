---
title: "Partitioning? Extended Partitions?"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by russet_wolf on 2009-02-22
My dad's got me working on his new laptop, partitioning it like he wants and running three OSes. The machine came with Vista, but he prefers XP and at my urging wants to have Ubuntu as well. But here is my problem: My dad wants these partitions:

1. Vista
2. XP
3. Ubuntu
4. Data
5. Backups

Unfortunately it is only possible to make four primary partitions on the disk, and I have read somewhere that only one can be extended. Since Ubuntu installs in an extended partiton, how can I work around this? If I could get Ubuntu to run as a primary partition, I would put Data and Backups into an extended partition as logical drives. Both of these need to be accessed by all three OSes.

Suggestions would be wonderful!

---

### Post by cariboo on 2009-02-22
Your Setup should be pretty simple, put XP, Vista and Ubuntu on primary partitions and Data and Backups on extended partitions. I would suggest installing XP first, just partion enough for XP, then install Vista and create a partition with enough space for Vista. Then install Ubuntu and use the manual partitioning option to create partitons for Ubuntu, swap, Data and Backups. I would suggest you format the Data and  Backups partitions as NTFS.

Jim

---

### Post by russet_wolf on 2009-02-22
Do you mean putting Ubuntu, the swap, Data and Backup partitions all in one extended partition?

---

### Post by caljohnsmith on 2009-02-22
> **russet_wolf said:**
> Do you mean putting Ubuntu, the swap, Data and Backup partitions all in one extended partition?
It's totally OK to install Ubuntu to the extended partition; Ubuntu does not need a primary partition. I would do just as you say, putting Ubuntu, swap, Data, and all your backup partitions in the extended partition. Good luck and let us know how it goes.

---

### Post by Mark Phelps on 2009-02-23
> **russet_wolf said:**
> 
Suggestions would be wonderful!

Just be sure that when you shrink the Vista OS partition to make room for the other stuff that you use the Vista disk management tool, not GParted or the Ubuntu installer.  Using the latter runs the risk of corrupting your Vista boot, which is easily repaired if you have a Vista DVD and can boot into it to run Startup Repair.  But if you don't have that DVD (and folks with preinstalled Vista generally do NOT), and your Vista OS gets corrupted, you will not be able to boot into it again.

For hints on workarounds to the Vista disk management tool shrinking problem, see the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by russet_wolf on 2009-02-27
Thank you everybody! My dad's been using his computer and is very satisfied with the results! Everything worked out wonderfully.

---

