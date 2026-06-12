---
title: "madwifi-ng VAP not running in monitor mode"
date: 2010-09-10
forum: Hardware
---

### Post by joaomluz on 2010-09-10
How i can put the madwifi-ng VAP drive in monitor mode?

I got this error:

> root@Joao:~# airmon-ng start ath0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
716    NetworkManager
733    avahi-daemon
736    avahi-daemon
839    wpa_supplicant
1176    dhclient
Process with PID 1176 (dhclient) is running on interface ath0


Interface    Chipset        Driver

**ath0        Atheros        madwifi-ng VAP (parent: wifi0) (VAP cannot be put in monitor mode)**


---

