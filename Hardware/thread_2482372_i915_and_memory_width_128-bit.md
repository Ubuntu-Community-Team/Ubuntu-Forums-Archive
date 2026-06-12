---
title: "i915 and memory width 128-bit"
date: 2022-12-29
forum: Hardware
---

### Post by pljushevij on 2022-12-29
Hello
My system is:
CPU - i5-7400
M/B - Gigabyte H110M-S2V
2x4GB DDR4 RAM
OS - Ubuntu Server x64 18.04.6

I was checked - graphical bus width is 64-bit. How to enable 128-bit for build in CPU graphic Intel HD 630?
How I can check, that Intel HD630 bus width is 64-bit? With this command:
sudo lshw -C display | grep width
Result is:
width: 64 bits

Ram working in dual channel mode. Was checking with this command:
sudo dmidecode | grep Interleaved
Result is:
Interleaved Data Depth: 2
Interleaved Data Depth: 2

Help me please.
Thank you

---

