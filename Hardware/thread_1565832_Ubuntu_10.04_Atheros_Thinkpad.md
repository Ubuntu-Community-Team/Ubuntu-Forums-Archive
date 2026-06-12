---
title: "Ubuntu 10.04 Atheros Thinkpad"
date: 2010-09-01
forum: Hardware
---

### Post by sntitus on 2010-09-01
I'm new to Ubuntu but had 8.04 running fine on my IBM Thinkpad R40.  Tried updating to 8.10 long ago, lost wireless and went back to my original installation.  

Installed 10.04 and saw the wireless issue not working again, system log telling me DHCP taking too long.

Beat myself up trying to figure out ndiswrapper and madwifi, etc.  I'm no pro.

Found an obscure post regarding blacklisted items.  I edited /etc/modprobe.d/blacklist_ath_pci.conf to comment out the line: blacklist ath_pci

Wireless now works

Wish I could tell you more but figured I'd post this if it makes a difference to someone else.

---

