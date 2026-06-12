---
title: "Intel i7 7560u - slow performance"
date: 2017-04-06
forum: Hardware
---

### Post by kristof-de-middelaer on 2017-04-06
Hello,

I bought a Dell XPS13 9360 with an Intel i7 7560u CPU which has the Iris Plus 640 integrated graphics unit. 

I wanted to dual boot this with Ubuntu 16.04 and did this by performing the regular steps: created a new partition for installing Linux, put the SSD in AHCI mode and installed ubuntu via usb.

However, after logging in it soon became clear that there were performance issues: opening a terminal literally takes 2 seconds, opening chrome about 6 seconds and dmenu_run takes about 4 seconds to open. My previous laptop (which is 4 years old) all opened these nearly instantly. I thought maybe the CPU frequency scaling was the culprit but even in 'performance mode' the problems persisted. 

I now think I have traced it to possible driver issues: the latest Intel graphics drivers are from Q4 2016 and my 7560u chip with Iris Plus 640 has only been on the market since january 2017. Am I right to assume these problems are due to suitable drivers not being available?

Performance on Windows is snappy, as expected.

---

### Post by kc1di on 2017-04-08
You may want to try installing a newer kernel try 4.10 
[this page ]("https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu")will tell you how to install a little utility that will make that easy. 
Good Luck.
P.S. before you update the kernel make sure dkms is installed so it will build the modules you'll need for your hardware.

---

