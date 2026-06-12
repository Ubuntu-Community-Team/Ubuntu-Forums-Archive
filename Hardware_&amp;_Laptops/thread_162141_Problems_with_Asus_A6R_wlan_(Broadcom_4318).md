---
title: "Problems with Asus A6R wlan (Broadcom 4318)"
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by cleth on 2006-04-18
I've had Ubuntu for two days now and I've been satisfied so far. **Except** for the wireless chip, which is Broadcom 4318. I've followed instructions [here]("http://www.ubuntuforums.org/showthread.php?t=31926") and [here]("http://ubuntuforums.org/showthread.php?t=25683"), and everything seems to install OK. 

```
sudo iwlist wlan0 scan
```

displays my AP correctly, so the card drivers which I downloaded from Asus website  seem to be working ok(?). But, ```
sudo dhclient wlan0
``` gives output of:

```
There is already a pid file /var/run/dhclient.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:15:f2:10:a1:70
Sending on   LPF/wlan0/00:15:f2:10:a1:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So, although the chip seems to be working at some level I can't get any connection. Any suggestions?

---

### Post by cleth on 2006-04-21
Still no solution.

---

### Post by Blacktalon on 2006-04-21
I have the same card a Broadcom 4318, and the problem with mine is that my mechine knows I have something there but it declares it as "unknown".  I am afraid that I haven't found a solution to this problem yet but as soon as I know of how to get my laptop to identify the hardware I will let you know.


Good luck,
  ~Blacktalon

---

