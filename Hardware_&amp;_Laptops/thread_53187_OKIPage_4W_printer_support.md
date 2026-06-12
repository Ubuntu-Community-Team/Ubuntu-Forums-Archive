---
title: "OKIPage 4W printer support"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by Rogz on 2005-07-30
I just tried (and failed) to install my OKIPage 4W printer on my fresh Horay-5.04 system using the **Computer -> System Configuration -> Printing tool**. The printer is detected, and I selected the suggested driver (oki4w) but when I try to print, nothing happens.

Viewing the */var/log/cups/error_log* (with debug2 set) gave me the following clue:
[I]D [30/Jul/2005:20:41:37 +0200] [Job 6] renderer command: (echo -n "AKEOKI PAPERSIZE=a4\nAKEOKI MANUALFEED=OFF\nAKEOKI PAPERWEIGHT=0\nAKEOKI GRAPHICS=OFF\nAKEOKI DARKNESS=0\n"; cat) 1>/dev/oki4drv 2>/dev/null
[/I]
since the */dev/oki4drv* device doesn't exist, I tried changing the driver to point to the port where my printer is connected, */dev/lp0*. This time I came up with:
[I]D [30/Jul/2005:20:27:22 +0200] [Job 4] renderer command: (echo -n "AKEOKI PAPERSIZE=a4\nAKEOKI MANUALFEED=OFF\nAKEOKI PAPERWEIGHT=0\nAKEOKI GRAPHICS=OFF\nAKEOKI DARKNESS=0\n"; cat) 1>/dev/lp0 2>/dev/null
D [30/Jul/2005:20:27:22 +0200] [Job 4] sh: line 1: /dev/lp0: Device or resource busy
[/I]
which is more strange since both lpq and the graphical client tells me that the printer is *Ready*. I'm not sure how I can investigate this problem any further since my knowledge in CUPS is rather limited.

I can provide the logs upon request if you need more to go on.

Thanks in advance
  Roger

---

