---
title: "Intrepid: Random disk device naming"
date: 2008-11-12
forum: General Help
---

### Post by y-man on 2008-11-12
Fresh install.
I have one of each of PATA and SATA drives in my box. One root partition only. Both / and /home partitions are on PATA drive. Install put the GRUB on the MBR of SATA drive.

Boot, and operation is fine. However an annoying random assignment of device names is happening. I mean /dev/sda is sometimes SATA, in other times PATA drive. Every boot it goes one way or other randomly, and about 50/50 frequency either way.

My search thru, kernel, and Ubuntu bug reporting systems did not yield anything. I filed an Ubuntu bug (#297192).

I'll be happy to hear any workaround/confirmation/ideas etc.

Thanks.

---

