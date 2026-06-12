---
title: "Trying to set up RAID, hanging boot"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by jtrask on 2006-01-20
I've just finished constructing a new AMD64 system with two 120gb WD hard drives. The mobo is a BFG nForce 4 Ultra, and it's got onboard soft RAID, so I wanted to set them up in RAID-0. I went through manual partitioning in the installation (good time to mention I'm fairly new to Linux in general? ;)) and created a 50mb ext2 boot partition (bootable :)) and a 1gig swap. I then put the rest of that hard drive and all of the other as physical devices for RAID, then went into the RAID manager and created md0 from that space. After that finished, I set up ext3 on the RAID space and the rest of the installation ran smoothly. After the installation completed I rebooted and it seems to be going alright, but hangs on GRUB loading. Any tips?
Thanks.

---

