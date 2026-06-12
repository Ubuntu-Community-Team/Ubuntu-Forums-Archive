---
title: "No network connection at all"
date: 2010-01-25
forum: Hardware
---

### Post by rainfactor on 2010-01-25
Hello

I have a 6930 Acer Aspire and i just installed |Karmic on it
I have no network connectivity at all
the only available connection according to the network manager is the VPN
ifconfig gives me just the loopback status
lspci tells me my wireless and my ethernet are  :

7.00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09,00,0 Ethernet controller : Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

dmesg |grep Atheros  shows nothing
dmesg| grep Intel shows : 
14.842245 iwlagn: Intel (R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
14857877 iwlagn 0000:07:00.0: Detected Intel Wireless WiFI Link 5100AGN REV=0xCEB9F6EA



If anyone has any suggestions/ideas to get this fixed, i will really appreciate it.

Thank You!

---

### Post by rainfactor on 2010-01-26
Resolved

 Bug #457760 

According to bugs.lunchpad :     acer aspire 6930 karmic. network hardware not recognized. No lan or wlan. Works in Jaunty

Network problem seems to be solved with new kernel. 

Fixed  by downloading kernel 2.6.32

---

### Post by oneup on 2010-01-30
Can anyone tell me if 8.04.4 latest release now has drivers for Attansic L2  Ethernet built in card,no connection possible,My Mobo is fairly new !

---

