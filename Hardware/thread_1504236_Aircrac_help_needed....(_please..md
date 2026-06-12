---
title: "Aircrac help needed....:( please."
date: 2010-06-07
forum: Hardware
---

### Post by heartyalex on 2010-06-07
Hi,

I would really appreciate some help. I have a laptop installed with wubi desktop 10.04. I am trying to install aircrack-ng. I am having some issues with the post installation when i am trying use sudo commands.

1. heartyalex@ubuntu:~$ sudo airmon-ng start wlan0
[sudo] password for heartyalex: 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
798    avahi-daemon
799    avahi-daemon
935    wpa_supplicant
2871    NetworkManager
4747    dhclient
Process with PID 4747 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        Unknown         wl

The driver states wl(?). I dont quite understand the reason and how to get around it. I did refer couple of articles and found that it was the driver issue. Can some one help with me with steps to change it.

This is my wireless card details.

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d4100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb



When i try a perl program by alex rhodes (crackwepwithperl)...this is another error i get..


heartyalex@ubuntu:~$ cd crackwepwithperl
heartyalex@ubuntu:~/crackwepwithperl$ perl crackwep.pl
Aircrack Frontend V.3
Obtaining wireless interface information... 
Run it as root
Run it as root
Run it as root
Run it as root
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


I really appreciate if any one could help me with this. Thanks.

---

### Post by hydroxph on 2011-11-03
Try this guide.

```
http://ubuntuforums.org/showthread.php?p=11420710
```

---

### Post by nothingspecial on 2011-11-03
aircrack-ng is not supported here.

Closed.

---

