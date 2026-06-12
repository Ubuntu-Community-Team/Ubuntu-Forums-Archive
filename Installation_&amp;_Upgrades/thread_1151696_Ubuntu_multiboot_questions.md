---
title: "Ubuntu multiboot questions"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by lovinglinux on 2009-05-07
After testing Windows 7 RC, I'm ready to remove it, but I want to use it's partition for multibooting different Ubuntu releases.

This is my current scheme:

[color=#33CCFF]/dev/sda1 ext3 /home/lovinglinux/videos[/color]
[color=#99FF99]/dev/sda2 ntfs[/color]

[color=#990000]/dev/sdb1 linux-swap[/color]
[color=#000099]/dev/sdb2 ext4 /
/dev/sdb3 ext4 /home[/color]

Since I already have 3 primary partitions, I will format sda2 as an extended partition and create 3 primary ext3 partitions inside it. Then I will install a different Ubuntu version on each, using the same linux-swap from sdb1, but I don't want to share the home partition between each installation. So I need to know how do I mount them.

I'm assuming I will have to select the manual partitioning method. Can I have multiple partitions mounted as root or they will conflict with each other? Since I already have a separate partition for /home, will it be automatically mounted on every new version I install (I don't want this)? How exactly do I mount the same swap for all of them?

---

### Post by dandnsmith on 2009-05-07
You can have as many root partitions/filesystems as you want - but can only use one at a time.

In the install, select the partition for root, that for /home (making sure it isn't set to be formatted), and that for swap.
Then just proceed with the installation.

---

### Post by lovinglinux on 2009-05-07
Thanks. Everything went well.

---

