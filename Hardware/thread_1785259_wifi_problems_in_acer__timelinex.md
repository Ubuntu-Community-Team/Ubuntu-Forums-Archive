---
title: "wifi problems in acer  timelinex"
date: 2011-06-18
forum: Hardware
---

### Post by pramod lekkala on 2011-06-18
hi am new to linux 

i myself bought a new laptop acer timelinex 4820TG 

and installed ubuntu as my cousin wanted 

but the issue is no internet connectivity

the wifi symbol wasn't there 
i googled and found out a lot has to be done to get wifi running on my machine

if so, can anyone be kind enough to tell me what exactly has to be done to get wifi running on my machine in laymen terms

coz am not a comp geniuses like you people 
thanks

my rfkill list details

0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no
1: acer-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

---

### Post by DanneStrat on 2011-06-18
Hi.

Could you post output from:

```
lspci
```

```
ifconfig
```

```
sudo lshw -c Network
```

---

