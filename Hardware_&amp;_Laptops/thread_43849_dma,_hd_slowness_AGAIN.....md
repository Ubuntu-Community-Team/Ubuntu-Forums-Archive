---
title: "dma, hd slowness AGAIN...."
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by solusrex on 2005-06-23
Finally! Ubuntu seemed to answer all my prayers. So much so that I deleted my XP partitions and threw away the install CDs. Alas it looks like I might have to go back to my second favourite, Fedora.

See, I have the problem that almost every other Ubuntu user has judging by all the various forums. HD is about as slow as an Acorn Electron. DMA is turned on, yet whenever I even so much as move a 1k text file the computer either hangs or, really annoyingly, stops playing whatever mp3 I am listening to at the time. Might sound trivial but I simply cannot listen to music on any of my laptops anymore. I never had this problem with Slackware, Mandrake, Fedora, etc. If anyone can help me please do otherwise Ubuntu goes for good... [-X

---

### Post by elvis on 2005-06-24
There's a slight chance it's not DMA, and is something completely unrelated.

For instance, on some recent 2.6 kernels on systems using Realtek cards, there was exceptionally high I/O loads on a system.  Likewise for 2.6.9 and a kernel paging problem.

What kernel are you using?  ("uname -r" will tell you) and have you tried upgrading to something more recent?

---

### Post by luca_linux on 2005-06-24
Try:
```
sudo hdparm -c1 -d1 -m16 -u1 -X69 -W1 /dev/hda
```
If you have problems try -W0 instead of -W1.
Note that you have to save the config in /etc/hdparm.conf if you don't want to set the hdparm flags on every boot.

---

