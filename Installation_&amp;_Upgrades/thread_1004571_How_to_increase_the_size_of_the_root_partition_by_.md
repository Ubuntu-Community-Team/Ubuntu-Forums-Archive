---
title: "How to increase the size of the root partition by creating a new home partition?"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by kpothi on 2008-12-07
Hi all,

**Background:** I've been using Ubuntu 8.04 for the past 6 months without any issues (I even tried 8.10 but came back to dear old 8.04). Initially when I installed it (Ubuntu 8.04), I didn't realize that I would stick with it for a long time and there would be a need to increase the size of the root partition (or a separate home partition).

**Current Status:**
Here is the output of 'sudo fdisk -l'
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4590    36864000    7  HPFS/NTFS
/dev/sda2            4591        4838     1992060   82  Linux swap / Solaris
/dev/sda3            4839        7328    20000925   83  Linux
/dev/sda4            7329        9729    19286032+   5  Extended
/dev/sda5            7329        7950     4996183+  83  Linux
/dev/sda6            7951        9729    14289786   83  Linux

sda1- Vista that I didn't login for the past 4 months.
sda2 - Swap
sda3 - Ubuntu 8.04
sda5 & sda6 - For testing new distributions.

**My Requirements:**
I'd like to increase the size of the root partition by creating a separate new home partition in sda1 (of course, after deleting Vista in sda1). I'd like to move the entire data from my current home folder into that separate home partition. Thus, I'll have plenty of space in the root partition.

Any idea to implement this? Or any other idea to increase the size of the root partition?

Thanks in advance.

Pothi.

---

