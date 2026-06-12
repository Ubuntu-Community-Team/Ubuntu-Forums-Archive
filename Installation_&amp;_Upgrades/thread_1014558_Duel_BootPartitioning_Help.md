---
title: "Duel Boot/Partitioning Help"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Pezwickie on 2008-12-17
Hello,

I'm currently running the live CD configuration for Ubuntu, but I'd like to install it as a duel boot for my Dell Inspiron 1520.

I'm terrified of doing the partitioning process wrong, and thereby screwing up my computer.  When i currently check what the partitions are, i have the following data:

/dev/sda1 0% (Shown as blue)
/dev/sda2 6% (shown as green)
/dev/sda3 91% (shown as orange)
/dev/sda5 1% (shown as blue)

I assume that sda3 is the vista partition.

If i wanted to set aside 10GB for Ubuntu from the Vista partition, would i just (after selecting "Manual" from step 4 of 7 in the install process) subtract 10,000 MB from the current partition size?

---

### Post by Yardarm on 2008-12-17
There should be an option in the partioning setup to guide you through resizing the partition.  It will show you a slider bar that you can use to adjust the size of your Windows/Ubuntu partitions and should handle everything automatically so you don't need to worry about doing a manual setup.

---

