---
title: "acer extensa2300 ipw2200 wireless problem"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by sargeras on 2007-06-19
Hello all, I have been trying to get wireless to work on my friends acer extensa2300 laptop computer.  I know that it is supposed to work out of the box, but for us it is not.  If I run lspci, the wireless card is detected.  Under lsmod, I also see the ieee80211 and ipw2200 entries.  The problem is, I get nothing from iwconfig, and ipconfig only shows eth0 (wired) and Lo.  Both dmesg and the log file do not report any errors either.  It appears as though the card is not turned on.  I have tried pressing the external power button, but to no avail.    I have set (according to another post here) the light indicator to toggle with the switch.  The light does not come on, and I receive no indications that wireless has been turned on if I press the button.  Any help would be appreciated.

Regards

---

### Post by wieman01 on 2007-06-19
Post the results of this:
> sudo iwlist scan

---

### Post by sargeras on 2007-06-20
The results from     sudo iwlist scan


Lo       interface doesnt support scanning

eth0   interface doesnt support scanning



That is all it says

regards

---

### Post by wieman01 on 2007-06-20
That's bad news. It's turned off as you have mentioned.

---

### Post by wieman01 on 2007-06-20
Could you post the output of this:
> sudo lshw
This is what I've got:
>            *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG
                vendor: Intel Corporation
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth1
                version: 05
                serial: 00:12:f0:38:3c:df
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 ip=172.18.166.210 multicast=yes wireless=IEEE 802.11b
                resources: iomemory:e0206000-e0206fff irq:9


---

### Post by sargeras on 2007-06-21
This is what I get from the lshw command, 



 *-network:1 UNCLAIMED
                description: Ethernet controller
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 4
                bus info: pci@02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32
                resources: ioport:3800-381f iomemory:e0203800-e020381f iomemory:e0203000-e02037ff irq:10


thanks for the support

---

### Post by wieman01 on 2007-06-21
> **sargeras said:**
> This is what I get from the lshw command, 



 *-network:1 UNCLAIMED
                description: Ethernet controller
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 4
                bus info: pci@02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32
                resources: ioport:3800-381f iomemory:e0203800-e020381f iomemory:e0203000-e02037ff irq:10


thanks for the support
Well, this is not a IPW2200 (Intel) but a INPROCOMM... Linksys. I think you will have to install it using other means, possibly "ndiswrapper". Can you find any information concerning it on the web?

There is something I have found:

[http://forums.suselinuxsupport.de/index.php?showtopic=19517]("http://forums.suselinuxsupport.de/index.php?showtopic=19517")
[http://ubuntuforums.org/archive/index.php/t-133492.html]("http://ubuntuforums.org/archive/index.php/t-133492.html")

---

### Post by sargeras on 2007-06-21
My appologies, that I didn't catch that earlier.  Thanks for the help, I'll take a look at your links and browse around again (this time for the correct card).

regards

---

