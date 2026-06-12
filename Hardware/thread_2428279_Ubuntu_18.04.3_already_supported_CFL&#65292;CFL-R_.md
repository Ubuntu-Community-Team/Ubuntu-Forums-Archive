---
title: "Ubuntu 18.04.3 already supported CFL&#65292;CFL-R (Coffee Lake Refresh) CPU or not."
date: 2019-10-02
forum: Hardware
---

### Post by ginousi on 2019-10-02
We would like to know the Ubuntu 18.04.3 already supported CFL&#65292;CFL-R (CoffeeLake Refresh) CPU or not.
If Ubuntu 18.04.3 not support CFL, CFL-R already, has roadmap when to support it?

We use CFL-R CPU (Intel i7-9700E) to install Ubuntu 18.04.3, then continue to do shutdown, Wake On LAN for stress test.
in several hundred cycle, system will hang in Ubuntu Logo when login  (Keyboard no function), or system will stay in Ubuntu Logo when login  (keyboard has function).

System information:
Ubuntu Desktop 18.04.3.
Kernel is 5.0.0-25, 5.0.0-29.
CPU Intel CFL-R i7-9700E, CFL i7-8700.

A. System stay in Ubuntu Logo when login,
we ctrl+alt+del to reboot, and boot to Ubuntu Desktop, then run journalctl to get log.
journalctl -b -1 > SystemStayLogoBootLog-b-1.txt (the boot log, system stay in Ubuntu Logo when Login). 
[https://drive.google.com/open?id=1nG...hR86CL_qzplDtS]("https://drive.google.com/open?id=1nG0YlQtpdWJaZWuHAfhR86CL_qzplDtS")
journalctl -b -2 > SystemBeforeStayLogoBootLog-b-2.txt  (the boot log, normal to boot into Ubuntu Desktop).
 [https://drive.google.com/open?id=1MO...gSbwcA533Q6otT]("https://drive.google.com/open?id=1MOQf1RcEhrdXK_78xHgSbwcA533Q6otT")
Check 2 logs, we noticed a fail message in boot fail log is "i965_dri.so does not support the 0xffffffff PCI ID."

B. System Hang when login,
Force to shutdown and reboot, and boot to Ubuntu Desktop, then run journactl to get log.
journalctl -b -1 > SystemHangLoginBootLog-b-1.txt (the boot log, system hang in when Login).
[https://drive.google.com/open?id=1OK...A3b7maD5Nb6JwV]("https://drive.google.com/open?id=1OKebWbRJR8PHvsi8SXA3b7maD5Nb6JwV")
journalclt -b -2 > SystemBeforeHangLoginBootLog-b-2.txt (the boot log, not mormal to boot into Ubuntu Desktop).
[https://drive.google.com/open?id=1_f...wh5fr_h-ovJ7LE]("https://drive.google.com/open?id=1_f0wmo1cuAc9nXA2Oiwh5fr_h-ovJ7LE")
Check 2 logs, we noticed that when system hang, Ubuntu is stop before below action
"kernel: Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k SSFS"

Cloud you kindly help to check logs and give us comments?

---

### Post by mörgæs on 2019-10-02
Hi, welcome to the fora.

With hardware as new as yours I would suggest trying at least 19.04, maybe 19.10.

---

### Post by ginousi on 2019-10-08
Hi, 

We use CFL-R CPU with Ubuntu 19.04 not encounter hang during Wake On LAN stress test.
(with Ubuntu 18.04.3 will encounter hang during Wake On LAN stress test.)
 
We check Ubuntu 19.04 release note, cannot find information about update for CFL-R CPU,
Could you kindly share some fix/update information related this issue?

---

### Post by mörgæs on 2019-10-08
I don't know anything in particular for these CPU's but if you follow the rule 'new hardware should have new software' then you are on the right track.

18.04 serves a purpose for old and semi-old hardware.

---

### Post by oldfred on 2019-10-08
What brand/model motherboard?
Some need additional UEFI settings or boot parameters.

Have you updated UEFI firmware? And if SSD, SSD firmware?

What video card or Intel video?

In 2017 Coffeelake tests, needed parameter then, but should not now:
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

You may want this, if older kernel used.
 i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer

---

### Post by ginousi on 2019-10-14
Per our experiments result, Ubuntu 18.04.2 (kernel 4.18.0-15) pass,
Ubuntu 18.04.3 (kernel 5.0.0-23, 5.0.0-25, 5.0.0-27, 5.0.0-29) system stop or hangs at reboot sometimes, 
Ubuntu 19.04 (kernel 5.0.0-29) pass. 

The phenomenon seems is related to Ubuntu version,

2 questions we want to check, 
1. Another user ever encountered the same phenomenon?
2. Ubuntu 18.04.3 has this known issue?

Please kindly tell us.

---

