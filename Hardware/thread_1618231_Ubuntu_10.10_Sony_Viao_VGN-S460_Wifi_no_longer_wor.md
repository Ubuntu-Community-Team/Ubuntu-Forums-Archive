---
title: "Ubuntu 10.10 Sony Viao VGN-S460 Wifi no longer works"
date: 2010-11-10
forum: Hardware
---

### Post by greendusk on 2010-11-10
Fixed
[http://www.linuxforums.org/forum/debian-linux/80014-intel-wireless-problems.html](http://www.linuxforums.org/forum/debian-linux/80014-intel-wireless-problems.html)

Download and Reinstall firmware 
-Download Lastest from 
[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
-Untar and copy [B]/lib/firmware/

[/B]This is the 2nd time this has happened. I turned of my laptop and when it turns back on I have no wireless. The 1st time it was on day one of install a clean ubuntu install but now i am two weeks in and don't want to re install. 



Here some info from lspci and the logs
lspci 

06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


Greb ipw2200 /var/log/messages

Nov 10 10:22:23 Computer-05 kernel: [   13.000489] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Nov 10 10:22:23 Computer-05 kernel: [   13.000494] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Nov 10 10:22:23 Computer-05 kernel: [   13.038820] ipw2200 0000:06:0b.0: power state changed by ACPI to D0
Nov 10 10:22:23 Computer-05 kernel: [   13.038833] ipw2200 0000:06:0b.0: power state changed by ACPI to D0
Nov 10 10:22:23 Computer-05 kernel: [   13.038858] ipw2200 0000:06:0b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 10 10:22:23 Computer-05 kernel: [   14.288048] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Nov 10 10:22:23 Computer-05 kernel: [   14.368982] ipw2200 0000:06:0b.0: PCI INT A disabled
Nov 10 10:22:23 Computer-05 kernel: [   14.369023] ipw2200: probe of 0000:06:0b.0 failed with error -5

---

