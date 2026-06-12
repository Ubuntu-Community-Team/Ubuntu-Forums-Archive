---
title: "specific external monitor not recognized ( max resolution 1024 x 768 )"
date: 2015-09-28
forum: Hardware
---

### Post by wondrash on 2015-09-28
First time poster, have mercy if I missed something.

**HW:**
HP Zbook G2 14''
hybrid graphics Intel + AMD Firepro M4130
monitor: Acer XB270HU 27'' 2560x1440 - display port only

_**Problem: external monitor not recognized ("unkown display"), works, but only at 1024x768 resolution (goal: 2560 x 1440)**_

**Note:**
I have a dual boot (Trusty + Win7). Under windows the Acer monitor gets recognized and works without any problems, hence I conclude the hardware/cable is not faulty.
Other external monitors (2 tested - one VGA and one DP) with resolutions greater than 1024x768 were recognized and worked without problems even in Ubuntu.


[B]Attempts at solution:
- xrandr
[/B] I have tried the usual boogie (cvt, xrandr --newmode, --addmode, --output), but inserting anything with resolution higher than 1024x768 results in the monitor turning off (orange LED, black screen)
**- drivers**
I have been fairly unsuccesful here. With the basic drivers or fglrx package, nothing changes with regard to my problem.
Catalyst allowed for switching from Intel to AMD gpu, but nothing with regard to external monitor.
Installing AMD drivers from AMD webpage failed (it says I have a different gpu, which is nonsense).
Installing drivers from HP driver webpage failed (Zbook G2 drivers unavailable for linux, G1 available as *rpm - alien completes with few errors). Installation has problems with dependencies.. (I think, forgot to take notes :-X)
Updating Intel driver failed (some dependency problems).
**- switching of hybrid graphics**
behaved just the same way as with hybrid or with only Intel drivers installed
[B]- other distributions
[/B]Ubuntu 14.04, 14.10, 15.04, 15.10 (some beta version I found somewhere, fake or not) and Fedora 22 all behave the same way
[B]- aticonfig / modifying xorg.conf manually
[/B]I was unsusccesful here, usually ended up rebooting, but I assume that if xrandr does not work I can't expect a different result here.. or should I?
[B]- crying
[/B]:'(

Interestingly
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Opal PRO [Radeon R7 M260] [1002:6605] (rev ff)

...while AMD FirePro M4130 is present, not Radeon R7 M260. These should be similar and might be just the case of shared pci number, so probably of no consequence.

Any suggestions very welcome.

P.S.: I have searched **extensively** about this issue, but any remotely relevant links and discussions are either unanswered or are solved with xrandr

---

