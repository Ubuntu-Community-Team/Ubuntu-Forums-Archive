---
title: "Reading a FreeBSD disc in Ubuntu"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by drzorc on 2007-09-06
I have a drive I pulled from a dying FreeBSD machine, and stuck it on my Ubuntu system (7.04) to try and recover some data. The drive isn't super happy, but I managed to get bios to see it, and after using testdisk to fix the partition table, I have /dev/hd and /dev/hdc1. My problem is, there is a single slice on that partition, and its not showing up. I've read on the internet that I should have a /dev/hdc1a, but I don't seem to have it. Is there a utility or something that can read slices off a FreeBSD disk, or should I go looking for a FreeBSD system to try to recover data with?

TIA

---

### Post by pay on 2007-09-07
Freebsd use different partition formats than Linux. There might be a way to make linux read it but I think you would be better off just getting a freeBSD system to read it natively.

---

