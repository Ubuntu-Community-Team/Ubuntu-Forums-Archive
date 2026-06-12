---
title: "MediaTek 7610 WiFi Not Working"
date: 2016-05-21
forum: Hardware
---

### Post by ustulation on 2016-05-21
My laptop Lenvo Y50-70 does has RealTek wireless card which does not support 5GHz signal. I got an external USB MediaTek powered WiFi Adapter (The box reads AC600 WiFi - Dual band) and installed device drivers. When i rebooted only the 2GHz networks were showing just like before. So i blacklisted rtlwifi and rtl8723be by putting the blacklist file in `/etc/modprobe.d/blacklist-my.conf`. Now on reboot, unless i plug in my usb adapter, it does not even show Enable/Disable WiFi option - so that's fine, It now depends on my USB adapter instead of the built-in. But the problem is the green light is continuously on, on the USB Adapter (not blinking) and it does not detect any WiFi around (no 2 GHz no 5 GHz etc).

I got and installed the driver[ according to this.]("http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/")

So in brief:
```
1) git clone https://sanrath@bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit.git
2) make && sudo make install
```

What else do i need to do to get it to detect surrounding WiFi signals ?

Here are the outputs:
```

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

uname -r
3.16.0-71-generic

lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0e8d:7610 MediaTek Inc. 
Bus 003 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 174f:14b8 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod | grep 7610
mt7610u_sta           854166  1

cat /etc/modprobe.d/blacklist-my.conf 
blacklist rtlwifi
blacklist rtl8723be

ifconfig
eth0      Link encap:Ethernet  HWaddr f0:76:1c:18:8b:d4  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f276:1cff:fe18:8bd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8197008 (8.1 MB)  TX bytes:1159387 (1.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72697 (72.6 KB)  TX bytes:72697 (72.6 KB)

ra0       Link encap:Ethernet  HWaddr 80:3f:5d:16:7f:3e  
          inet6 addr: fe80::823f:5dff:fe16:7f3e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:19872 (19.8 KB)

iwconfig
eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"MT7610U_STA"
          Mode:Auto  Frequency=5.26 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.
```

---

