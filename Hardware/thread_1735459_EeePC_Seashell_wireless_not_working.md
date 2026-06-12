---
title: "EeePC Seashell wireless not working"
date: 2011-04-21
forum: Hardware
---

### Post by wisnoskij on 2011-04-21
Hello,

I a trying to get Ubuntu 10.04 working on a family members new netbook.

The only real problem I have encountered thus far is the wireless is not working (it worked when booted to windows).

I have been to ([https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)) and still have a few question and have not been able to get anywhere.

Here is my command output:
~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbffc000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:9f:ec:23
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.13  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)


How I read this is that I have a working Atheros Ethernet card, but a not working Broadcom wireless car.
But strangely the page does not show any Broadcom fixes and does show fixes for Atheros cards.
So am I supposed to ignore the Broadcom and just assume I have a Atheros? I tried this and following the steps did not seem to accomplish anything.

And I am not sure exacly what model it is, it does not say anywhere on the machine but it has ASUS on the top panel (which I think narrows down the possibilities a little). But if you need the model type I am sure I could find it out.

Any help would be appreciated.

Jonathon Wisnoski

---

### Post by wisnoskij on 2011-04-26
Still looking for a solution to this problem.

---

### Post by barrieluv on 2011-04-26
Turn the machine over and it will have a grey/silver sticker with the model number on it.  The two I have in front of me say 10005HA and 10005P.  Both have Atheros wireless cards and both work out of the box with Ubuntu 10.04 and 10.10.  
If you have a 1008 model it may require the Broadcom drivers which you can get by plugging your machine into the router via ethernet and going to System > Administration > Additional drivers.

---

