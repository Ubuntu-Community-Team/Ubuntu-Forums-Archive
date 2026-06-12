---
title: "Toughbook CF-29"
date: 2010-12-21
forum: Hardware
---

### Post by Fir3chi3f on 2010-12-21
Well I got everything working, until I closed the lid- the screen was black when I opened it back up and after a hard reboot the wireless and wired internet doesn't work. 

I've been fallowing the guide here, but they don't mention sleep not working or problems with wired/wireless.
[http://forum.notebookreview.com/panasonic/496467-cf-29-ubuntu-10-4-success.html](http://forum.notebookreview.com/panasonic/496467-cf-29-ubuntu-10-4-success.html)

From lspci, Network controllers are:
Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] (rev 05)
Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)

ifconfig only lists the loopback adapter "lo"

Any ideas how to get the ethernet or wireless working again? Or how to make sleep work properly?


note: I installed netbook remix package on top of the original ubuntu desktop. -Although I don't think that had any sort of effect besides looks.

---

