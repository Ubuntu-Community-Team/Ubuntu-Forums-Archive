---
title: "Very slow sleep/resume/restart with Nvidia driver"
date: 2014-12-27
forum: Hardware
---

### Post by pumrel on 2014-12-27
Hello,
I've just bought my wife a new computer and wanted to install Ubuntu on it. I chose the LTS 14.04 version as recommended which then booted into software mode which I guess is due to GT 730 not being supported by *nouveau* in that version. Sleep and resume were super fast though. Then I installed the Nvidia driver and that's when the problems started. I installed the 340 version from xorg/edgers because I read that the support for GT 730 was added in 340.17 or so. Sleep, resume and also shutdown and restart are very slow and take about 30s. I first though that it might be a kernel problem but it happens with 3.17.1 as well. I really don't know how to debug this and dmesg doesn't give me any hint except the statement ```
NMI watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [kworker/u4:12:2479]
``` which I really don't know what it means.
Same thing happens in 14.10 which I ditched completely because of another issue with plymouth and that was just too much for me. Same issue in Mint 17.1
I have attached just *dmesg *for now as I don't know what else might be helpfuls.

Specs:
Intel Pentium G3220
GIGABYTE GT730, 2GB DDR5
Gigabyte H81M-S2H

---

### Post by barkerson on 2014-12-28
Well, it DID say in your attatched file that "nss-myhostname" wasn't installed. I'm not sure what it is but installing that is a beginning.

---

### Post by pumrel on 2014-12-28
> **barkerson said:**
> Well, it DID say in your attatched file that "nss-myhostname" wasn't installed. I'm not sure what it is but installing that is a beginning.

That is over 50 minuter after wakeup and seems to be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1277608"). It is of no importance. 
In the meantime I tried another PSU and that doesn't seem to be the problem.

---

