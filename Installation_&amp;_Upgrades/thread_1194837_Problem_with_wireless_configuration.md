---
title: "Problem with wireless configuration"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by vasudev on 2009-06-23
hello forum members,

Today i re-installed ubuntu 8.10 in my system, everything is working fine but only my wireless is not working can any body please help me to rectify this problem. 
My laptop is Fujitsu Siemens Amilo.

 **lspci** command give following output
......
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
.........

dmesg  grep 2200 shows
[   26.724088] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.724100] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.725445] ipw2200 0000:01:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   26.739099] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.739231] firmware: requesting ipw2200-bss.fw
[   33.043473] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[  361.996042] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[  363.012055] ipw2200: Failed to send CARD_DISABLE: Command timed out.

---

### Post by mk1w86 on 2009-06-24
Was the wireless working when you were running Ubuntu 8.10 before?  You could also try Ubuntu 9.04 which might work.

---

### Post by vasudev on 2009-06-24
Yes it was working before...

---

