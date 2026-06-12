---
title: "Amilo Pro Edition V3505 + Atheros AR5001 WIFI issue"
date: 2011-01-27
forum: Hardware
---

### Post by doomster on 2011-01-27
hello. i just installed ubuntu 10.10 on my laptop. i use an external wifi usb card to post this msg, as my internal doesnt seem to be turned on.


here are 
```
doomster@cryobot:~$ lshw -C network
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan1
       version: 01
       serial: 00:15:af:87:b4:8e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d4000000-d400ffff

```
and
```
doomster@cryobot:~$ lspci
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

also my rfkill list is off```
doomster@cryobot:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
and my lsmod list shows my driver as loaded, and  my iwconfig output is
```
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

sorry if  i got you tired. any ideas why i cant get it to show me wireless networks when i disconnect my external wifi card?
i have a HW button for wifi (not switch) and a combinaion of FN+F10 that dnt do anything

---

### Post by doomster on 2011-01-28
it seems that i had switched off the wifi when i had a windows installation on the pc, and it was somehow in off state. after alot of searching around i found a guy that gave me the solution i wanted to share it 
with you for further knowledge.
This turned on my card:
```
sudo modprobe fsam7400 radio=1 
```

and this way i turn it on on boot:
```
sudo echo fsam7400 >> /etc/modules

sudo echo options fsam7400 radio=1 >> /etc/modprobe.d/options
```

many thanks to Odzangba Kafui Dake  for the solution

---

### Post by shokalabutcha on 2011-06-14
Hi,

I had a similar problem. Whenever I did "rfkill unblock all", my wireless would go from 
Soft blocked: Yes
Hard blocked: No

to 

Soft blocked: No
Hard blocked: Yes

Tantalizing, isn't it? In the end, I created the following script as a (barely acceptable) solution:

sudo rmmod -f ath5k
sudo rfkill unblock all
sudo odprobe ath5k

I hope this script helps someone. If anybody knows how to make this permanent, that will be much appreciated.

I am using a Natty Narwhal, (Ubuntu 11.04) running on Fujitsu Siemens Amilo PA3515 with an Atheros AR5001 wireless module.

Hope this helps,
Shoka

---

