---
title: "Troubles with installation after MBR modification"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Zverko on 2009-11-08
Long story short: Karmic Koala netbook remix hangs after launching installation. Cursor flashes, computer doesn't respond to anything except forced power off.

Long story full: it all started out good and I was really stupid. :(

Got brand-new netbook with WinXP OEM install. Installed netbook remix with resizing partition and grub multiboot. Everything was fine (I haven't tested ubuntu installation fully, but it didn't give me any troubles while installing).

Then I decided to resize partitions once again. And did it from under Windows. I.e. I've just deleted whole Ubuntu partition (planning to reinstall it later) and created one more ntfs partition for data storage... forgot about grub totally. So next time I boot netbook I see "no valid filesystem" and grub rescue console. :(

After five long hours of teeth grinding and messing with lots of unix and win software I've managed to launch [paragon's disk manager]("http://www.paragon-software.com/home/hdm-professional/") and use "Update MBR" button. Well, good news is that after that I can boot to my WinXP partition without any troubles (at least haven't seen one). Bad (and somewhat strange) news is that now I can't launch Ubuntu installation. :(

Any ideas, anyone?

HP Mini 311

Original partition setup:
- original MBR
- 160 Gb Primary NTFS with WinXP

Second partition setup:
- grub
- 40 Gb Primary NTFS with WinXP
- 120 Gb for ext4 and swap

Current partition setup:
- fixed (?) MBR
- 40 Gb Primary NTFS with WinXP
- 80 Gb NTFS logical drive
- 40 Gb of non-partioned space

---

