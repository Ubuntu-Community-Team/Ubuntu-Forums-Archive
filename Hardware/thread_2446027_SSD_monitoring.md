---
title: "SSD monitoring??"
date: 2020-06-23
forum: Hardware
---

### Post by 2912pwil on 2020-06-23
I've installed Crucial P2 NVME in my Dell laptop, Ubuntu now booting off it, very quick!

Any tools for monitoring the hardware - temperature etc? Under Windoze there' Crucial's "Storage Execuitve" which DOES support P2.  I've tried GSmartControl which monitors HDD but not my SDD. It's Crucial P2 500GB PCIe M.2 2280SS SSD, CT500P2SSD8

Appreciate Linux tends to stress hardware less than Windows, but it was noticeably warm when copying some folders.

Regards & thanks in advance

---

### Post by Yellow Pasque on 2020-06-23
If you only have one SSD:
```
sudo apt-get install nvme-cli
sudo nvme smart-log /dev/nvme0
```
If you have mutiple drives, figure out which one you are interested in:
```
sudo nvme list
```

On my Debian sid install, the temps for the nvme drives started showing up in my 'sensors' output at some point (the capability was probably added with newer kernels)

---

### Post by 2912pwil on 2020-06-24
Excellent! Thanks, much obliged!

---

