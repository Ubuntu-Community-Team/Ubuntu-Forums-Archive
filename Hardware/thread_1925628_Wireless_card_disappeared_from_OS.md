---
title: "Wireless card disappeared from OS"
date: 2012-02-14
forum: Hardware
---

### Post by AncientPC on 2012-02-14
My mother uses an old Asus EEE PC 1000HA with UNR 10.04 Lucid to watch YouTube. This model is notorious for having wireless driver problems which I managed to fix using ndiswrapper and these [instructions]("http://ubuntuforums.org/showthread.php?t=1191178").

After two years, wireless has stopped working. I have double checked that the physical wireless switch on the laptop is turned on.

```

&#9581;&#9472;root@nanking ~  
&#9584;&#9472;&#10148;  lshw -C network                                                                                                   2012.02.14 20:25:04 CST 
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:f6:ee:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fbfc0000-fbffffff ioport:ec00(size=128)

&#9581;&#9472;root@nanking ~  
&#9584;&#9472;&#10148;  lspci | grep Ethernet                                                                                             2012.02.14 20:26:25 CST 
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

```

I'm not sure how the wireless card could have just disappeared and am open to any suggestions.

---

### Post by varunendra on 2012-02-16
> **AncientPC said:**
> 
```
lspci | grep Ethernet
```I'm not sure how the wireless card could have just disappeared and am open to any suggestions.
Firstly, that command should only have 'net', not 'ethernet', because wireless adapter is not ethernet. So the correct form would be-
```
lspci | grep -i net
```
Even better (to list the associated bus and driver as well):
```
lspci -nnk | grep -iA2 net
```

However, since lshw doesn't show it, I don't think lspci could either. A couple of quick checks:

[LIST]
[*]Go into BIOS and see if it appears there and is enabled
[*][This page]("http://www.notebookreview.com/default.asp?newsID=4655") suggests the wireless card is located in a user-accessible area > A single panel houses the hard drive, wireless  card, and single ram slot, making the process of swapping out the parts  as painless as possible.. Open the panel and make sure the card is seated properly.
[*]If both these checks come out ok, try a live cd/usb to see if it is detected there.
[/LIST]

---

### Post by AncientPC on 2012-02-17
Thanks. I'm working remotely so I can't inspect the laptop physically, and there's only so much I can ask my mom to do. I'll definitely do these suggestions the first chance I get.

---

