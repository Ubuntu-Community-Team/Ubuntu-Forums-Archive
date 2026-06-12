---
title: "Partitioning for ubunto on XP machine"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by fin1 on 2009-10-26
Hi guys,

I need to install ubuntu for school purposes and im just about to do it but i have a couple of questions i haven't found answers for so i would appreciate any help.
First - what type of partitions does ubuntu need? can both the system and the swap partitions be logical or do i need them to be primary? If so can they be on the same extended partition together with WIN logical drives? what limitions, if any, do i have regarding partitions' size, type and location?

Im attaching a screenshot of my HDDs status, if anyone can recommend where and how to create the partitions it would be great.

btw, is there a way to create the ubuntu partitions in advance through win xp with something like partition magic and then just direct the installation there?

Thanks very much!

---

### Post by pricetech on 2009-10-26
Ubuntu can make its partitions at install time.  That's probably the easiest way to do it.  Defrag XP first and expect XP to complain and run chkdisk the first time you boot to it after installing Ubuntu.

---

### Post by fancypiper on 2009-10-26
It doesn't matter where the partitions are, just that they exist.
I suggest 3 partitions:
/ - 10-20 GB depending upon amount of software installed.
swap - 2 GB (probably too much, but I have a 1 TB drove)
/home - the rest of the empty drive space
If you have other drive(s), I would put them on /windows, /pub, /storage or some such.
I would choose either ext4 or ext3 for the Linux partitions.

See [Wikipedia Ext4]("http://en.wikipedia.org/wiki/Ext4").

Any partitioning tool should work OK, I used fdisk on a live linux cd to partition and change the filesystem type, and mkfs to format them.  I believe you can find how to use the utilities on the ubuntu live install disk with a quick search of these forums.

Choose the manual partitioning option when you start the install and the partitioner starts.

---

### Post by Zoot7 on 2009-10-26
Ubuntu needs a system partition and a swap partition.

The best thing to do if you're unsure IMO is allocate some space for ubuntu beforehand using something like gparted to do so. Then install it but use the option "Most Continous Free Space" upon installing Ubuntu, it'll do the rest for you. ;)

---

### Post by oldfred on 2009-10-27
All the suggestions above are good. You will have your windows partitions to use for data as Ubuntu will read/write those without problems.
Windows requires primary partitions, Ubuntu works fine from either primary or logical.
I like to have an operating system on every drive and in that drives MBR have the boot for that drive. If you reverse drives in BIOS when you install Ubuntu you will keep your windows install intact in the MBR and usable if you want to reverse the drives back. Ubuntu will find the windows install on the second drive and map it so windows still thinks it is first and works when you boot from that from grub.

---

