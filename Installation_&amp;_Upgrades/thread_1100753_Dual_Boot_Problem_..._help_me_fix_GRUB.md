---
title: "Dual Boot Problem ... help me fix GRUB"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by SkankinRatFink on 2009-03-19
Hello there. So here's the skinny ... on my new computer I installed Windows XP, then Ubuntu Studio. Obviously the GRUB worked just great at the time.

Then I had problems with XP and had to reinstall. You all know the deal-- Windows gets greedy and overwrites the MBR so the GRUB is gone.

I looked up this guide on dual-booting which assumes Linux was installed first and XP second. With the situation I'm now in, this is effectively the case. The [fifth page](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5) describes how to restore the GRUB. I ran a live CD (Linux Mint) and followed their steps exactly. At the grub command line, the command **setup (hd0)** gives me the following error. **Error 17: Cannot mount selected partition**. I don't know how to fix this! hd0 is the correct hard drive--- when I type in **root (hd0,0)** or **root (hd0,1)** it correctly describes the partitions on the hard drive.

Here is how my hard drive is partitioned, if it helps:
[IMG]http://i41.tinypic.com/2ewf9tl.png[/IMG]

**sda1** is my Windows XP partition.
**sda2** is my Linux (Ubuntu Studio) partition.
**sda3** is the partition containing the logical partitions ....
- **sda5** is Linux swap space.
- **sda6** is my storage partition for all my files (NTFS format)

Please help! I'd like to get Ubuntu Studio back as a boot option. Thanks a lot.

---

### Post by D3ath on 2009-03-19
```
find /boot/grub/stage1
```
should point you in the right direction for you HDD location!

If anything check this thread if that doesn't work
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by SkankinRatFink on 2009-03-19
Ohhh, I get it now. I saw your reply even before you edited it. The "find" command pointed me to hd(0,1) -- my Linux partition. As expected. **root hd(0,1)** followed by **setup (hd0)** did the trick. Thanks!

---

### Post by D3ath on 2009-03-19
> **SkankinRatFink said:**
> Ohhh, I get it now. I saw your reply even before you edited it. The "find" command pointed me to hd(0,1) -- my Linux partition. As expected. **root hd(0,1)** followed by **setup (hd0)** did the trick. Thanks!
not a problem! I'm happy that you are happy!

---

