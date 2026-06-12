---
title: "wireless connection"
date: 2008-11-07
forum: Hardware
---

### Post by Torleif67 on 2008-11-07
I have an HP G7000 laptop where i run Ubuntu 8.10 on. Everything works fine for me except that i cannot connect to the internet wireless. 

Under network connection, wired i have Autho eth0 but under wireless there is nothing displayed. I need help to set up my laptop so i can connect to the internet wireless with my D-Link Router.

Is there anybody around who knows anything about this who could please help me?

Torleif

---

### Post by Torleif67 on 2008-11-07
tell you the truth i do not know! I only know that i have a HP G7000 laptop computer. I am very new to this so thats way i ask for some help with this. Ubuntu is new but very nice to me and i do not know this so please help me.

Torleif

PS: How do i find this out???

---

### Post by Riqz on 2008-11-07
run 

```
sudo lshw -C network 
```

and post the output please.

---

### Post by Torleif67 on 2008-11-07
lybeth@lybeth-laptop:~$ sudo lshw -C network
[sudo] password for lybeth: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f5:44:86
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:38:f0:db:53:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
lybeth@lybeth-laptop:~$

---

### Post by Riqz on 2008-11-07
There is another thread of another guy with your wifi card with AR242 model nnumber. Click [here]("http://ubuntuforums.org/showthread.php?t=967654") to go to it! Hope this helps! apparently he solved the problem. Try to read the thread and everything should be explained.

Goodluck!

---

### Post by Torleif67 on 2008-11-17
Thank you very much for this, now my wireless works perfect!!!

---

