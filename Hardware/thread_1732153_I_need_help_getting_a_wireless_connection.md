---
title: "I need help getting a wireless connection"
date: 2011-04-17
forum: Hardware
---

### Post by angel t on 2011-04-17
hey all,

i am new to linux and ubuntu so i need a little help setting up a wireless connection.

here are the problems so far. 
i have gone under System> Administration and there is no network option only network tools
i have tried to follow along with some of the other forums and tutorials and they have not been any help at all.
my wired connection works just fine but for some reason i cant connect wirelessly

when i type in lswp this is what i get.... i have no idea what i need to do...

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:82:f7:bd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.5 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:fe5fe000-fe5fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:1b:0e:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

obviously my wireless interface is disabled but how do i get it enabled and get online wirelessly? any help could be great..
if it helps i have it installed on a dell inspiron 1521 computer that is using vista as its other operating system.. thank you :) 

\

---

### Post by Ghostmn on 2011-04-17
Have you checked if you can install a proprietary driver? System>administration>Hardware drivers. or System>preferences>hardware drivers. [Edit] Sorry I haven't used ubuntu in awhile, switched to arch =/ but i'm thinking you need the proprietary broadcom driver.

---

### Post by wolfen69 on 2011-04-18
> **Ghostmn said:**
> Have you checked if you can install a proprietary driver? System>administration>Hardware drivers. or System>preferences>hardware drivers. [Edit] Sorry I haven't used ubuntu in awhile, switched to arch =/ but i'm thinking you need the proprietary broadcom driver.

In ubuntu 10.10 it is System>Administration>Additional Drivers. You probably need the b43 drivers. After reboot, just click the network icon on your panel and you should see wireless networks.

---

### Post by dineshs on 2011-04-18
Ensure that the physical wireless switch is ON and enable wireless is ticked when you rightclick network manager icon on top right of the panel.
Remove ethernet cable.(I have read that Network manager gives preference to wired)
Run
```
sudo rfkill unblock all
rfkill list all
```

---

### Post by angel t on 2011-04-19
ok so when i logged on this afternoon an update came up that said there were proprietary drivers available and when i went to download/ install this message came up

  [B]Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb)  403  Forbidden [IP: 91.189.88.31 80]

and nothing got downloaded.

and dineshs, how do i turn my card on? and when i did that code in terminal this is what came up...

rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

im sorry this seems to be a pain and im grateful for all you peoples help.
[/B]

---

### Post by dineshs on 2011-04-20
> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu1_i386.deb) 403 Forbidden [IP: 91.189.88.31 80]
try again 
>  how do i turn my card onseems to be OK since it is not blocked.
Please unplug ethernet cable and post the result of ```
sudo lshw -C network
```and```
iwconfig
```

---

### Post by jquis8411 on 2011-04-20
It sounds like the repository may have been down, the link works now. It is possible that you need to enable the universe or multiverse (/system/admin/software sources) too. I dont think Dineshs was talking about your wireless card, I think he was referring to a wireless switch on your router. The rfkill list shows that everything is ok on your computer, at least as far as allowing a connection. I would try getting that driver again and try wolfen's directions.

If you are using a laptop you can toggle the wireless on and off, for example on mine it is a combination of fn+f2. Maybe this is what Dineshs meant.

---

### Post by angel t on 2011-04-22
when i tried to get the driver again it went through and connected automatically. thank you all for your help

---

