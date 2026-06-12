---
title: "Wireless networking on Packard Bell laptop"
date: 2008-10-06
forum: Hardware
---

### Post by hrMeyer on 2008-10-06
Hi.

I'm using a Packard Bell Easynote laptop, and am having trouble with Ubuntu and the wireless network card, (probably because of lack of driver). I.e. it is not working.

How can I fix this?

Thanks.

---

### Post by issih on 2008-10-06
Tell us the specs of the wireless hardware or at least the exact model of the notebook.

Ideally boot ubuntu and run the following command in a terminal:

```
sudo lshw -C network
```

enter your login password when prompted then post the output here, that ought to let us identify the manufacturer and model of your wireless hardware.

---

### Post by hrMeyer on 2008-10-06
This is the output.

```
fredrik@FredrikMeyerlaptop:~$ sudo lshw -C network
[sudo] password for fredrik: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:07:07.0
       logical name: eth0
       version: 10
       serial: 00:1f:c6:d7:03:75
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=193.157.232.177 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
```

I assume this is the information you asked for.

---

### Post by issih on 2008-10-06
Ok for that chipset you appear to have two options.

1) use ndiswrapper
2) use the latest madwifi drivers

If you installed the 64 bit version of ubuntu, you can only use 1) apparently.

the following thread contains good guides to using both methods:

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

Ndiswrapper is almost certainly easiest unless you are comfortable with compiling source code. The madwifi version might enable more advanced features of your hardware however...so its swings and roundabouts.

Hope that helps

---

### Post by hrMeyer on 2008-10-07
I'm not sure which version of Ubuntu I have, 64 or 32-bit. How can I check this?

However, thanks so far for answering.

---

### Post by issih on 2008-10-07
in a terminal run "uname -a", if the output contains "x86_64" or "ia64" then I think you are running the 64 bit version, otherwise you are probably running the 32 bit one

I'm not 100% sure on that though :s

---

