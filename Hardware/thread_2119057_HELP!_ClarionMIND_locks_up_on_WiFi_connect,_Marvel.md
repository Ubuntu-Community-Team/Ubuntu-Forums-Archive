---
title: "HELP! ClarionMIND: locks up on WiFi connect, Marvell SD8686"
date: 2013-02-22
forum: Hardware
---

### Post by BlackDiamond885 on 2013-02-22
I have a ClarionMIND I'm trying to get going for a friend.  Among other problems with trying to get Lubuntu 12.10 running on this machine (halts during reboot, non-working touch screen, GMA500 issues, etc), the biggest problem I need to fix first is the Marvel SD8686 wifi.

When I try to connect to a wireless network, the machine completely locks up.  It doesn't seem like NetworkManager can bring the card up either.  Both crda and NetworkManager lock up when the card is not up, I have to run 'ifconfip wlan0 up' manually.

Appreciate any help.

EDIT:  I figured it out finally.  Just needed another couple hours of grinding.  

According to linuxwireless.com, the libertas driver requires CMD_802_11_DATA_RATE which is not available in v9 firmware. I removed the sd8686_v9 firmwares so it will revert to the sd8686_v8.

---

