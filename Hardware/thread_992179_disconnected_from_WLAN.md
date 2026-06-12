---
title: "disconnected from WLAN"
date: 2008-11-24
forum: Hardware
---

### Post by joschum on 2008-11-24
Hello,

I installed Ubuntu 8.10 (intrepid) on a Lenovo ThinkPad T43p. I can connect via WLAN but after some minutes the connection breaks. The connection works fine on another ThinkPad (X300) so the access point should not be the source of the problem. After being disconnected a window pops up which is entitled "Wireless Network Authentication Required". When I click on the connect button the connection is sometimes restored but it might take a long time. Does anybody have an idea how to achieve a stable WLAN connection?

Hoping for help,
joschum

Here are the details of my wireless configuration:
```

root@thalamus:~# lspci -nn | grep -i net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
0b:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212 802.11abg NIC [168c:1014] (rev 01)
```

```
root@thalamus:~# egrep -v "^$|^#" /etc/network/interfaces
auto lo
iface lo inet loopback
```

```
root@thalamus:~# egrep -v "^$|^#" /etc/resolv.conf
nameserver 195.186.1.109
nameserver 195.186.4.109
```

```
root@thalamus:~# egrep -v "^$|^#" /etc/hosts
127.0.0.1	localhost
127.0.1.1	thalamus
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

After the connection is broken ifconfig yields:

```
ath0      Link encap:Ethernet  HWaddr 00:14:a4:39:42:f3  
          inet6 addr: fe80::214:a4ff:fe39:42f3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13885 (13.8 KB)  TX bytes:38001 (38.0 KB)
```

... and after reconnecting
```

ath0      Link encap:Ethernet  HWaddr 00:14:a4:39:42:f3  
          inet addr:192.168.254.100  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe39:42f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26796 (26.7 KB)  TX bytes:70582 (70.5 KB)
...

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-39-42-F3-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204578 errors:0 dropped:0 overruns:0 frame:17256
          TX packets:1743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:21907654 (21.9 MB)  TX bytes:157070 (157.0 KB)
          Interrupt:21 
```

```
root@thalamus:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.38.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.51.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.254.0   0.0.0.0         255.255.255.0   U     2      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.254.1   0.0.0.0         UG    0      0        0 ath0
```

```
root@thalamus:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"zup-wlan"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:11:5F:64   
          Bit Rate:48 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:19FD-0EE4-F98C-7337-B0B8-288F-3410-68DB   Security mode:restricted
          Power Management:off
          Link Quality=43/70  Signal level=-55 dBm  Noise level=-98 dBm
          Rx invalid nwid:201808  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

