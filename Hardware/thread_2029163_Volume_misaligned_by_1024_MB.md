---
title: "Volume misaligned by 1024 MB"
date: 2012-07-19
forum: Hardware
---

### Post by Degraan on 2012-07-19
I've created a partition to install Ubuntu on that I set as a generic 100000 MB. The extended volume I create says it's misaligned by 1024 MB and will have performance issues. I aligned it on MiB when I created it and it seems to have this issue regardless of partition size if I recreate it. I'm getting this error on Gparted running the Ubuntu 12.04 64bit live CD. Most of the posts I've found about it say it's because it was aligned on cylinders instead of MiB but I've made sure to check the align selection multiple times when creating the extended volume.

---

### Post by oldfred on 2012-07-19
If it is just the extended partition, do not worry about it. You do not write into the extended except thru all the logicals inside it. So if the logicals are ok then it is not an issue.

Unless you have a new 4K drive or SSD, I also do not think it matters.

---

