---
title: "RTL8723bu – can’t connect after suspend"
date: 2020-06-01
forum: Hardware
---

### Post by borntzal19961 on 2020-06-01
[COLOR=#242729][FONT=Arial]I have a laptop with Wi-FI – RTL8723bu. When I disconnect from the network or put my computer to sleep, connection is no longer possible until reboot. I have Ubuntu 20.04 with Kernel 5.4.0-33-generic.
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]alexandru-petrica@alexandrupetricabalan-MY8315XX:~$ sudo lshw -C network[/FONT][/COLOR]
[sudo] password for alexandru-petrica: 
  *-network                 
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlx18bb26a4faa5
       serial: 18:bb:26:a4:fa:a5
       capabilities: ethernet physical wireless [COLOR=#242729][FONT=Consolas]       configuration: broadcast=yes driver=rtl8723bu ip=192.168.100.11 multicast=yes wireless=IEEE 802.11bgn[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]

---

