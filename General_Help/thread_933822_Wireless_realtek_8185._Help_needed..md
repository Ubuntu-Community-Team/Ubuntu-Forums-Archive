---
title: "Wireless realtek 8185. Help needed."
date: 2008-09-29
forum: General Help
---

### Post by johnterdi on 2008-09-29
I need help getting my wireless connection up and running smoothly.

I installed Ubuntu last week, and I got the realtek 8185 working wondrously. It was not until I decided to uninstall Ubuntu, then I had the problem. After reinstalling the OS, I got my internet working again, but not for long. So now I need a little help.

Typing iwlist scan in terminal shows my wlan0 as installed. I connect to my router with all the details (ssid, pw, etc) entered, but I still get no network connection.

Please help.
(Oops. Earlier I posted this in another forum thinking it was Ubuntu's forum)

---

### Post by pytheas22 on 2008-09-30
It could be a DNS issue, if you're getting an IP address but are still unable to load web pages.  Please connect to your network, then post the output of the following commands:
```

cat /etc/resolv.conf
host google.com
ping google.com
ping 64.233.187.99
iwconfig
ifconfig
lshw -C Network
```

---

### Post by johnterdi on 2008-10-01
Here is the list:

```
cat /etc/resolv.conf
nameserver 10.15.2.1
nameserver 10.15.2.2


host google.com
;; connection timed out; no servers could be reached


ping google.com
ping: unknown host google.com

iwconfig
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power:24 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:42:3F:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29562 (28.8 KiB)  TX bytes:29562 (28.8 KiB)


lshw -C Network
  *-network
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:42:3f:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 multicast=yes
       resources: iomemory:d0100000-d0103fff ioport:a000-a0ff irq:16
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:d4:b3:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek,03/21/2008,5.1105.0321. latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11b
       resources: ioport:b000-b0ff iomemory:d0200000-d02001ff irq:18
```

The following commands when entered in the terminal, I get *No working leases in persistent database - sleeping* at the end of its output.

**sudo** iwconfig wlan0 mode Managed essid johnterdi key xxxxxxxxx
**sudo** dhclient

---

### Post by johnterdi on 2008-10-01
Hm.... That's odd. After using the commands ifconfig wlan0 down and enabling it again. Then entering the ssid and key, it doesn't work. But after restarting, It seems to run smoothly. I'm not sure that did it. The last time I tried, even restarting, it didn't even connect.

Well, I'm just happy that it's now connected. Thank you pytheas22, for taking your time to respond back to the thread. I appreciate it.

---

### Post by pytheas22 on 2008-10-01
Alright, I'm glad it's working now.  If it breaks again, please let me know.

---

