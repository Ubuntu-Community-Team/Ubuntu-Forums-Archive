---
title: "pccard/pcmcia problem - pavilion ze1110 - ubuntu dapper"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by croto on 2006-07-19
Hi, I couldn't find any thread about the problem I have. However, there're many people having problems with pccard/pcmcia. I have a HP Pavilion ZE1110. It shows a weird behaviour when I try to use the pcmcia network card Netgear FA511. Most of the times it doesn't work (the lights in the card are on, but the system doesn't see the network device), and freezes the computer with a kernel error. Occasionally, it does work, for no apparent reason. The randomness of the behaviour is really confusing. The system worked flawless on slackware 10, so it isn't a hardware problem.

I'm attaching with this post the output of lspci, and of dmesg for both cases: when the card works, I get dmesg_good.txt; when it doesn't I get dmesg_bad.txt. I singled out a line from dmesg_bad.txt which might be indicative of the problem:

PCI: Unable to reserve I/O region #1:100@1400 for device 0000:02:00.0

Has anyone encountered a similar problem? Any hints on how to solve it?

Thanks a lot.

---

