---
title: "Filesystem Corruption on 2nd Boot from USB Flash Install"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by yottabit on 2009-05-16
Hi Ubuntu Wizards!

I am attempting to lower my power bill, improve my TV watching experience, and save the environment all at once. I have an 8 GB USB flash drive onto which I'm attempting to install Mythbuntu.

The install goes perfectly, and the first boot is also just fine.

But that's where the bliss ends. During that first boot, I do an update of all software, and upon reboot, find that the filesystem is corrupted beyond repair.

I have tried this twice now... the first time I used Reiserfs, and the second time I used the tried & true ext3.

Any ideas why the 2nd boot would find such a corrupted filesystem? And how can I go about fixing it?

Some ideas I have: perhaps the shutdown of the OS on the first boot doesn't give sync enough time to flush the data to the flash, or perhaps as part of the shutdown and unloading/unmounting of drivers/devices the USB bus is reset or the volume is unmounted before the final sync...

But I don't have enough experience to start troubleshooting this...

---

