---
title: "Dell XPS M1530 no wireless"
date: 2009-12-07
forum: Hardware
---

### Post by genjix on 2009-12-07
Hey,

Brand new Dell XPS M1530 out the box and slap Ubuntu on it ASAP. Wireless isn't working.

I found this thread. [https://bugs.launchpad.net/dell/+bug/190664](https://bugs.launchpad.net/dell/+bug/190664)

I've installed the restricted Broadcom chipset and tried ndiswrapper but when I run,

```
# dhclient eth2
```

It just keeps trying and never connects.

Please help! :( brand new laptop.

---

### Post by genjix on 2009-12-07
bump

---

### Post by jsfour on 2009-12-07
I have a m1530 running solidly with 64bit karmic. You should be able to use the 14xx drivers, or if you want packet injection check out:

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

I hope this helps!

---

### Post by genjix on 2009-12-07
thank you! that's great news to know I can get it working :)

is this what you mean by 14xx driver?
[IMG]http://img248.imageshack.us/img248/2097/bcom.jpg[/IMG]

That gives me:
```
[code]root@the-accountant:~# iwconfig wlan2 essid theinternets
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan2 ; No such device.
root@the-accountant:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:14 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
root@the-accountant:~# dhclient eth2
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth2/00:26:5e:1a:ef:af
Sending on   LPF/eth2/00:26:5e:1a:ef:af
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@the-accountant:~# 
```
With my open network.

Not worried at all about packet injection since I have a USB wireless. Will try Karmic 64bit tomorrow when I get a CD.

---

