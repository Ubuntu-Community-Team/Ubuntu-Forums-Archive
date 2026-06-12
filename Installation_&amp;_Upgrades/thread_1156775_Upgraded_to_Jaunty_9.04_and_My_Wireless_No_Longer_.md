---
title: "Upgraded to Jaunty 9.04 and My Wireless No Longer Works"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by chiques on 2009-05-12
Hello Everyone,
I had my system to auto update. It updated my kernel to:

> 
chiques@chiques-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty
chiques@chiques-laptop:~$ 



ifconfig doesn't see my wireless card:

> 
chiques@chiques-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:8c:d1:0b  
          inet addr:192.166.1.100  Bcast:192.166.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe8c:d10b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2774052 (2.7 MB)  TX bytes:677835 (677.8 KB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:920 (920.0 B)  TX bytes:920 (920.0 B)

chiques@chiques-laptop:~$ 



But lshw -c network does ([COLOR="Red"]without a logical name though[/COLOR]:confused:):

> 
root@chiques-laptop:/home/chiques# lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       **logical name: pan0** {the ethernet works fine and it has a logical name....:( )
       serial: ba:91:04:00:94:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



I've read that b43-fwcutter needs to be reinstalled and I tried that using the package installer. I selected "Mark for Reinstall" but that still did not work. I would appreciate any suggestions.

---

### Post by chiques on 2009-05-12
A problem which is making most of the troubleshooting tutorials useless is that the command: 

```
lshw -C network
```

is expected to print a "logical name" as described in pre-requisite #4 of [[COLOR="Blue"]How To: Manual Network Configuration without the need for Network Manager[/COLOR]]("http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshoot+wireless") for my wireless card but it doesn't. There is a logical name for my ethernet connection which is working fine.


When I run this command I see:

```
root@chiques-laptop:/home/chiques# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:6f:b1:9c:ba:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


[I][B][COLOR="Red"][SIZE="3"]
All of these wireless problems began when I upgraded to Jaunty 9.04. [/SIZE][/COLOR][/B][/I]:icon_frown::icon_frown:



Is it possible to remove and reinstall the driver for my wireless card? I have the following wireless card detected.

```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

---

### Post by chiques on 2009-05-13
Hello ladies and gentlemen, 

This issue has been resolved. Out of all of the suggested recommendations, none of them worked. 

Here is the fix for my specific problem.


1. Power down the notebook

2. Turn off the wireless card (yes, switch it off)

2a. If you have a logic switch, power if off before you shut down.

3. Power up the notebook

4. Boot to the desktop (with the wireless card off)

5. Power on the wireless card through the physical switch. Wait a few seconds and you should see the indicator light on the notebook register as "on". You will then see the bar icon begin it's search for wireless networks and hard drive activity. 

6. At this point the local wireless network will be detected and if already configured it will connect to it.


Thanks for everyone's input.

---

### Post by Peter09 on 2009-05-13
The thing with lshw -C network is that it shows what driver is installed on the card.

---

### Post by chiques on 2009-05-13
Take a look at this, it might answer your question.

[http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)

---

