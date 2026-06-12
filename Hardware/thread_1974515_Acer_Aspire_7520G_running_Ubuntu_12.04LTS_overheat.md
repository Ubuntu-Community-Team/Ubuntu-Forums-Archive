---
title: "Acer Aspire 7520G running Ubuntu 12.04LTS overheat"
date: 2012-05-06
forum: Hardware
---

### Post by rgmno1 on 2012-05-06
Hello,

As the title says I am having an overheat problem with ubuntu 12.04LTS, the computer jumps from 50 degrees (normal temp) to 90 in about 10 minutes of watching a video... and, of course, shuts down....

My machine is an 
AMD Turion 64x2, 2.2GHz, 2x512 KB L2 cache
Nvidia GeForce 8600GS TurboCache 1280MB
4GB DDR2

I used 11.10 before with the same issue and I used jupiter software in power saving mode and that fixed the problem but after upgrading to 12.04 the software stopped working....

Please help.

---

### Post by rgmno1 on 2012-05-09
well I solved the problem by uninstalling and reinstalling jupiter and setting it to power saver mode. It is keeping the temperature at about 60 degrees even when watching a movie, but because it's on power saver my laptop isn't working at full capacity.

I sure hope someone will answer this with a better permanent solution.

BTW here is the code for jupiter
```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```
for those who need it

---

