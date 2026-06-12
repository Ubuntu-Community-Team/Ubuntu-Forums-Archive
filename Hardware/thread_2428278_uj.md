---
title: "uj"
date: 2019-10-02
forum: Hardware
---

### Post by ginousi on 2019-10-02
We would like to know the Ubuntu 18.04.3 already supported CFL&#65292;CFL-R (CoffeeLake Refresh) CPU or not.
If Ubuntu 18.04.3 not support CFL, CFL-R already, has roadmap when to support it?

We use CFL-R CPU (Intel i7-9700E) to install Ubuntu 18.04.3, then continue to do shutdown, Wake On LAN for stress test.
in several hundred cycle, system will hang in Ubuntu Logo when login (Keyboard no function), or system will stay in Ubuntu Logo when login (keyboard has function).

System information:
Ubuntu Desktop 18.04.3.
Kernel is 5.0.0-25, 5.0.0-29.
CPU Intel CFL-R i7-9700E, CFL i7-9700.

A. System stay in Ubuntu Logo when login,
we ctrl+alt+del to reboot, and boot to Ubuntu Desktop, then run journalctl to get log.
journalctl -b -1 > SystemStayLogoBootLog-b-1.txt (the boot log, system stay in Ubuntu Logo when Login). 
[https://drive.google.com/open?id=1nG0YlQtpdWJaZWuHAfhR86CL_qzplDtS](https://drive.google.com/open?id=1nG0YlQtpdWJaZWuHAfhR86CL_qzplDtS)
journalctl -b -2 > SystemBeforeStayLogoBootLog-b-2.txt  (the boot log, normal to boot into Ubuntu Desktop).
 [https://drive.google.com/open?id=1MOQf1RcEhrdXK_78xHgSbwcA533Q6otT](https://drive.google.com/open?id=1MOQf1RcEhrdXK_78xHgSbwcA533Q6otT)
Check 2 logs, we noticed a fail message in boot fail log is "i965_dri.so does not support the 0xffffffff PCI ID."

B. System Hang when login,
Force to shutdown and reboot, and boot to Ubuntu Desktop, then run journactl to get log.
journalctl -b -1 > SystemHangLoginBootLog-b-1.txt (the boot log, system hang in when Login).
[https://drive.google.com/open?id=1OKebWbRJR8PHvsi8SXA3b7maD5Nb6JwV](https://drive.google.com/open?id=1OKebWbRJR8PHvsi8SXA3b7maD5Nb6JwV)
journalclt -b -2 > SystemBeforeHangLoginBootLog-b-2.txt (the boot log, not mormal to boot into Ubuntu Desktop).
[https://drive.google.com/open?id=1_f0wmo1cuAc9nXA2Oiwh5fr_h-ovJ7LE](https://drive.google.com/open?id=1_f0wmo1cuAc9nXA2Oiwh5fr_h-ovJ7LE)
Check 2 logs, we noticed that when system hang, Ubuntu is stop before below action
"kernel: Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k SSFS"

Cloud you kindly help to check logs and give us comments?

---

### Post by howefield on 2019-10-02
Duplicate thread closed.

---

