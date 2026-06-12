---
title: "China &amp; wifi: can't connect ? ... bad password or else ?"
date: 2011-11-23
forum: Hardware
---

### Post by juju43 on 2011-11-23
Hello,

I'm using Ubuntu 11.04 (upgrade pending) on a samsung N230.
$ lspci -v |grep -i wireless
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

I had 2 strange connections problem as I'm travelling China
- a wifi with a SSID in chinese, I can't even see (either in network manager or in iwlist scan). A chinese windows computer saw it w/o problems.

- a wifi with "normal" alphanumeric characters. I can see it, passwd is also "normal", but can't connect. Connection was done again on a windows7 computer with same password and it works too.
Error messages from /var/log/syslog seems to say bad password but It was checked and typed again
Nov 23 21:17:29 netbook wpa_supplicant[839]: Trying to associate with e0:05:c5:bf:55:10 (SSID='GTX' freq=2422 MHz)
Nov 23 21:17:29 netbook wpa_supplicant[839]: Association request to the driver failed
Nov 23 21:17:29 netbook NetworkManager[652]: <info> (eth1): supplicant connection state:  scanning -> associating
Nov 23 21:17:29 netbook wpa_supplicant[839]: Associated with e0:05:c5:bf:55:10
Nov 23 21:17:29 netbook NetworkManager[652]: <info> (eth1): supplicant connection state:  associating -> associated
Nov 23 21:17:29 netbook NetworkManager[652]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Nov 23 21:17:32 netbook wpa_supplicant[839]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Nov 23 21:17:32 netbook wpa_supplicant[839]: CTRL-EVENT-DISCONNECTED bssid=e0:05:c5:bf:55:10 reason=0
Nov 23 21:17:32 netbook NetworkManager[652]: <info> (eth1): supplicant connection state:  4-way handshake -> disconnected
Nov 23 21:17:32 netbook NetworkManager[652]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Nov 23 21:17:33 netbook wpa_supplicant[839]: Trying to associate with e0:05:c5:bf:55:10 (SSID='GTX' freq=2422 MHz)
Nov 23 21:17:33 netbook NetworkManager[652]: <info> (eth1): supplicant connection state:  scanning -> associating
Nov 23 21:17:33 netbook wpa_supplicant[839]: Association request to the driver failed
Nov 23 21:17:33 netbook NetworkManager[652]: <warn> (eth1): link timed out.


My only idea is there is some chinese characters completion in the way, but Windows has no way display password after typing. still need to check a copy/paste from notepad.

Any ideas how to trace/debug those problems ?

Thanks.

---

