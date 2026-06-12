---
title: "rtl8187 freezes on wpa_supplicant &quot;CTRL-EVEN-SCAN-RESULTS&quot;"
date: 2010-03-15
forum: Hardware
---

### Post by Blue Matt0 on 2010-03-15
I have an Alfa AWUS036H (rtl8187) USB wifi card hooked up to an Ubuntu 9.10 amd64 desktop.  
It works great with no special driver modification, except every two minutes wpa_supplicant writes "CTRL-EVENT-SCAN-RESULTS" to syslog.  From approximately ten seconds before this message until this message appears, the wireless does not work at all.  iwconfig still shows wireless as connected, and route, ifconfig, etc show no changes.  This does not happen on my laptop (Macbook3,1 Ubuntu 9.10 amd64), or on windows using the same card, so it has to be an issue with the rtl8187 driver.  Any ideas on fixing this (or decreasing the frequency of wpa_supplicant's scans)?

---

