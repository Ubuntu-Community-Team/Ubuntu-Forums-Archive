---
title: "Hardy can't upgrade, &quot;not enough space on device&quot;"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by dkonrad on 2008-12-15
I've just installed Hardy and the updater tells me I need to update 210 packages. When I try to do so, the upgrade of the kernel fails with the "not enough space on device" message. I have plenty of space on all my partitions (fullest partition is 26% full), except for /boot. There I have 32M, which the docs tell me should be enough.

So, do I need more space on /boot, or is something else going on?

Thanks
Doug

---

### Post by Pumalite on 2008-12-15
Probably need to enlarge /boot.
Post:
sudo fdisk -lu
df -h

---

### Post by dkonrad on 2008-12-15
I'm not at that computer now; however df reports that /boot is 48% full. I will post more later. Thanks.

---

### Post by dkonrad on 2008-12-16
:-\" I created a new /boot partition of 128 MB. It all went smimmingly. Thanks!

---

