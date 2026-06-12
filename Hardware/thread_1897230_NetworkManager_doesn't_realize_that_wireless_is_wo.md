---
title: "NetworkManager doesn't realize that wireless is working fine"
date: 2011-12-18
forum: Hardware
---

### Post by Ohnodoctor on 2011-12-18
Hello there. I'm having a bit of trouble with NetworkManager, I think. Whenever I go into system settings and try to enable the wireless, it goes to 'on' briefly, and then flips back to off. Here is some stuff that I found in /var/log/syslog that seemed relevant:
```
Dec 18 18:21:53 ubuntu NetworkManager[871]: <info> (wlan0): bringing up device.
Dec 18 18:21:53 ubuntu kernel: [  650.961872] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
Dec 18 18:21:53 ubuntu kernel: [  650.961882] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
Dec 18 18:21:53 ubuntu kernel: [  650.965263] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Dec 18 18:21:53 ubuntu kernel: [  650.965413] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 18 18:21:53 ubuntu NetworkManager[871]: <info> WiFi hardware radio set enabled
Dec 18 18:21:53 ubuntu NetworkManager[871]: <info> WiFi now enabled by radio killswitch
Dec 18 18:21:53 ubuntu NetworkManager[871]: <info> (wlan0): supplicant interface state: starting -> ready
Dec 18 18:21:53 ubuntu NetworkManager[871]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 18 18:21:53 ubuntu NetworkManager[871]: <info> (wlan0): supplicant interface state: ready -> inactive
Dec 18 18:21:54 ubuntu NetworkManager[871]: <info> WiFi now disabled by radio killswitch
Dec 18 18:21:54 ubuntu NetworkManager[871]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Dec 18 18:21:54 ubuntu NetworkManager[871]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 18 18:21:54 ubuntu NetworkManager[871]: <info> (wlan0): taking down device.
Dec 18 18:21:54 ubuntu dhclient: receive_packet failed on wlan0: Network is down
```
However, when I bring the wireless up manually, it works just fine!
```
root@ubuntu:~# ifconfig wlan0 up
root@ubuntu:~# iwconfig wlan0 essid "mywifi"
root@ubuntu:~# dhclient wlan0
root@ubuntu:~# ping 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=57 time=26.9 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=57 time=17.2 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=57 time=16.5 ms
^C
--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 16.588/20.255/26.911/4.714 ms

root@ubuntu:~# lspci | grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
root@ubuntu:~# 
```
Any help would be appreciated :)

---

