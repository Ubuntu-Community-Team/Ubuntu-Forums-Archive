---
title: "ubuntu not recognizing partitions"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by -spy on 2009-07-19
I have 2 partitions on my harddrive , C and F, I want to install Ubuntu over my old Windows 7 beta partition (:C).

When I put the ubuntu disk in, and boot from the dvd, and go through the installation procedure it doesn't show that my hdd is partitioned. It wants me to manually partition it as if it where just one.

My question is why isn't my :c partition showing? Am I supposed to go through a different installation procedure? Basically all I want to do is be able to select ":c" and complete replace it with Ubuntu.

---

### Post by cariboo on 2009-07-19
Linux does not use drive letters, what does show up when you use gparted? I suspect if you have 2 partitions they should show as /dev/sda1 and /dev/sda2.

---

### Post by -spy on 2009-07-19
> **cariboo907 said:**
> Linux does not use drive letters, what does show up when you use gparted? I suspect if you have 2 partitions they should show as /dev/sda1 and /dev/sda2.

Not sure, but I do remember stuff similar to what you posted "/dev'" etc. and think that may be what ubuntu uses instead of letters. (my actual partitions are Windows 7 Local disk :C, Recovery : D, and Win 7 beta :F)

 Would I be able to install Ubuntu inside windows, wubi, then when I choose to full install, could I select the specific partition.

---

