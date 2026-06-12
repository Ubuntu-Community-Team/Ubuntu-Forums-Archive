---
title: "&quot;wireless is disabled by hardware switch&quot; - New to Linux"
date: 2011-07-31
forum: Hardware
---

### Post by alex95 on 2011-07-31
Hi everyone,

I've just got started with using Ubuntu within the past few hours and am already really impressed. However, I seem to be not able to use the wireless.

As I'm new to Linux, I'm new to terminal and what not, so I followed a few things I found online and got this..

```
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


If someone could explain what I need to do to get this working, I'd be really grateful..

~ Alex

---

### Post by Dobro_player on 2011-07-31
Is there a switch on your computer that turns the wireless on and off?

---

### Post by varunendra on 2011-08-01
> **alex95 said:**
> 
```
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Open a terminal and enter this command:
```
sudo rfkill unblock wifi
```

Then recheck using **rfkill list all** to see if it is still blocked.

---

### Post by alex95 on 2011-08-01
Thanks for the replies guys. The button is already turned on, and I have tried turning it on and off but no changes. I've also tried 

```
sudo rfkill unblock wifi
```

Which still comes up with the same list again. Could I be missing drivers?

---

### Post by varunendra on 2011-08-01
What if you do:
```
sudo rfkill unblock all
```

As for driver confirmation, post output of:
```
sudo lshw -C network
```

---

### Post by alex95 on 2011-08-01
Thanks for the quick-reply once again.. When I did **sudo lshw -C network** I got this.. I think I did something wrong?

** PCI (sysfs)**

Thanks again, really appreciated!


EDIT. There was a window below it..


```
  description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:7e:44:d4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.86 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:2c:4a:85
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff
```

---

### Post by varunendra on 2011-08-01
> **alex95 said:**
> 
```

  *-network **DISABLED**
       description: Wireless interface
       **product: AR5001** Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
....
....
....**driver=ath5k** driverversion=2.6.38-10-generic **firmware=N/A** latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff
```
The message you got initially is normal. The above output is what I needed. The firmware=N/A looks suspicious to me. More outputs please :) :-
```
ifconfig -a
``````
iwconfig
``````
lsmod | grep ath
``````
dmesg | grep -Ei "ath|wlan"
```Also, some laptops have an inbuilt BIOS function which disables wireless when it detects an Ethernet connection. So, are you connected to LAN via Ethernet? If so, try disconnecting it from the wired connection then retry with:
```
sudo ifconfig wlan0 up
```

---

