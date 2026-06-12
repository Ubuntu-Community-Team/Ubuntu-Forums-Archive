---
title: "can't connect to secured wifi network"
date: 2009-09-10
forum: Hardware
---

### Post by pacman401 on 2009-09-10
Hello
I have problem with connecting to secured wifi network with my router provides for me
```
 sudo iwconfig wlan0 key s:my_key
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
```
*key contains non hex characters a-z*

here is all procedure step by step
```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid my_essid
sudo iwconfig wlan0 key s:my_key
[I]Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.[/I]

```
tested on ubuntu 9.04 (64bit) minicd
lshw
```

*-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:1f:3b:4b:b5:d9
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```
lspci
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```
my router is Dlink DI-524
wireless settings of router
SSID broadcast Disabled
Network ID(SSID) my_essid
Channel 6
Security WPA-PSK/WPA2-PSK
Preshare Key my_key

same error in command line I have got on ubuntu 9.10 and ubuntu 9.04
although
a graphic network manager ubuntu 9.04/9.10 is connecting me correctly with no problems

---

