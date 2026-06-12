---
title: "Problem with HP 620 internal speakers"
date: 2010-09-13
forum: Hardware
---

### Post by wamefefe on 2010-09-13
Hi all. I installed ubuntu 10 on my hp 620 notebook but there is a problem with my internal speakers. The internal speakers have no output but when I plug in external speakers, it does work. Any help on how to make the internal speakers work will be highly appreciated.

---

### Post by vmonkey on 2010-09-22
To solve this problem you should:

1) download and install "http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip"

2) run "**sudo apt-get install linux-backports-modules-alsa-lucid-generic**" without the quotes (this will make sound work even after kernel update. If you have any problems, try to do the first step again)

Note: Sound works then only after restart.

---

### Post by deonsmalberger on 2010-10-19
I tried all the above and i still do not have sound on my HP 620. Please assist:confused:

---

### Post by dfgvdfgsd on 2010-10-28
I have the same problem...and I'm using Windows 7 :o

---

### Post by revenge_2006 on 2011-11-19
I have the same problem, can anyone help please. I want to know what to do?? ... is it even a software or a hardware problem. Please help . Thanks

---

### Post by arnold255 on 2011-12-04
Hi,
You can read here [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/269027]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027")

Hope you can do it.

---

