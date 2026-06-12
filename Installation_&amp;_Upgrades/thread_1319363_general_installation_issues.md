---
title: "general installation issues"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by louigi600 on 2009-11-08
Just wanted to report some installation issues I ran into while installing UNR 9.10 on my Acer AspireOne:

1) Installation wanted to do ext4 on flash device (journaling filesystems meant for normal disk mass storage are generally a bad thing to run on flash devices)

2) Installation from the live running system took over 5 hours (and I was installing from a USB cdrom onto a pretty fast MMC+ card)

3) Installation did not worn me in any way that the default initrd would not be able to boot from /dev/mmcblk<x> device that I was installing to .... that was veru annoying after such a long install process .... I was able to work around the problem by making a custom initrd

---

