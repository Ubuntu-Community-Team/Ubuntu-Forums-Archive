---
title: "ipw2200: Unable to load ucode"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by Commuto on 2006-03-08
I plugged an additionnal Intel Pro Wireless 2200 BG mini-PCI card in my laptop, a Toshiba 5105-S501. This device has been running fine with Windows for 2 years.

Now as a Debian user I try to switch to Ubuntu and come upon a problem with it. My periphericals recognition went very, very well, apart from this IPW2200.
It is listed in lspci:
```
me@myhost:~$ lspci | grep 2200
0000:02:0a.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

```
and modules are loaded:
```
me@myhost:~$ lsmod | grep ipw2200
ipw2200               103880  0
firmware_class          9952  1 ipw2200
ieee80211              29380  1 ipw2200
ieee80211_crypt         5604  2 ipw2200,ieee80211
me@myhost:~$

```
However no wireless ethernet interface at all:
```
me@myhost:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:41:17:89
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
***<cut>***

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
***<cut>***

me@myhost:~$

``` (eth0 is my LAN connection)

And there is a strange message in dmesg... which I guess is a lead to the issue:
```
me@myhost:~$ dmesg | grep ipw2200
[4294708.444000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294708.444000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294708.452000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[COLOR="Magenta"][4294708.834000] ipw2200: Unable to load ucode
[4294708.834000] ipw2200: Unable to load firmware: 0xFFFFFFEA
[4294708.834000] ipw2200: failed to register network device
[4294708.872000] ipw2200: probe of 0000:02:0a.0 failed with error -5[/COLOR]
me@myhost:~$

```Apprently it fails to load the firmware (?)

Last thing, the firmware location (or is it ???) :
```
me@myhost:/lib/hotplug/firmware$ ls *2.3*
ipw-2.3-boot.fw-2.6.12-10-686       ipw-2.3-ibss.fw-2.6.12-9-686
ipw-2.3-boot.fw-2.6.12-9-686        ipw-2.3-ibss_ucode.fw-2.6.12-10-686
ipw-2.3-bss.fw-2.6.12-10-686        ipw-2.3-ibss_ucode.fw-2.6.12-9-686
ipw-2.3-bss.fw-2.6.12-9-686         ipw-2.3-sniffer.fw-2.6.12-10-686
ipw-2.3-bss_ucode.fw-2.6.12-10-686  ipw-2.3-sniffer.fw-2.6.12-9-686
ipw-2.3-bss_ucode.fw-2.6.12-9-686   ipw-2.3-sniffer_ucode.fw-2.6.12-10-686
ipw-2.3-ibss.fw-2.6.12-10-686       ipw-2.3-sniffer_ucode.fw-2.6.12-9-686
me@myhost:/lib/hotplug/firmware$
```
They are here!! :cry:  
Seems weird to me... and to you? :eek:

---

### Post by Commuto on 2006-03-09
Bump.
Any idea where I can dig further (log files, ...) ?

---

### Post by sdb2028 on 2006-03-09
Try this thread> [http://ubuntuforums.org/showthread.php?t=138760](http://ubuntuforums.org/showthread.php?t=138760)

---

### Post by Commuto on 2006-03-09
As far as I understood your thread I comply with your settings. My system is a totally fresh install, therefore didn't change anything.

Still the problem keeps bouncing. Weird :???:

---

### Post by Commuto on 2006-03-11
*Bum*. Any idea, any place, any one ? :mrgreen:

---

