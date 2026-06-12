---
title: "Intel Core 2 Quad Q6600 install problems"
date: 2015-07-20
forum: Hardware
---

### Post by sickofthebluescreen on 2015-07-20
**Hello,**
I am having compatibility issues with a clients Intel Motherboard. I can install ubuntu normally but soon after first boot I get graphics lock ups constantly and everything looks pixalated. I am guessing this is a linux graphics issue and the strange thing is that there is no option to install intel graphics in ubuntu 15.04 on... can anybody help me out? If you have installed with this processor before, what worked best for you? I've tried everything and Ubuntu doesn't work right and I get the same problems in Mint as well. Please help! =)

---

### Post by dino99 on 2015-07-20
Please give us the output of the 2 below commands

 in a terminal, run :
> lspci | grep VGA
> sudo lshw -C display

there is no related cpu trouble here (q6600 does not provide graphics)

---

