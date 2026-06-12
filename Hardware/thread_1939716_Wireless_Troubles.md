---
title: "Wireless Troubles"
date: 2012-03-12
forum: Hardware
---

### Post by joecmp on 2012-03-12
Hi everyone. Sorry for the double post, I didn't see this forum before posting this thread in the general help section. Anyways, I recently installed ubuntu 11.10 on my laptop and I've  been having some trouble with my wireless from time to time. I've got  all of the most recent updates, and downloaded several essential  packages when I first installed. It works most of the time but  occasionally when I log on or wake my computer up after its been  hibernating for a while my wireless connection is gone. When I go to the  network configuration it doesn't even register that I have wireless.  The only way I've been able to get it to start working again is by  rebooting the machine. When my wireless is working and I open up  terminal and enter the command lshw -c network this is the output:
```
joe@joe-laptop:~$ sudo lshw -c network
[sudo] password for joe: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:ef:20:54
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth  driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1  multicast=yes port=MII
       resources: irq:42 memory:f6488000-f6488fff ioport:30f8(size=:cool: memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:96:4b:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k  driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.5 latency=0  link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f6000000-f600ffff

```I haven't tried that command when my wireless isn't working, I  would but I dont have control of when it happens. I'd like to apologize  in advance if someone has posted about this issue already, I wasn't able  to find it. Any help is greatly appreciated. Oh, and if it makes a  difference, I'm running on a compaq presario F700 series laptop.

---

### Post by grahammechanical on 2012-03-12
Do you see this?

> driver=ath5k

That tells us that you have a driver installed. Or to put it another way, Ubuntu recognizes and can use the wireless adapter. This is very important.

So, why does it only use this wireless adapter sometimes? Is the wireless adapter being switched by the hardware/computer?

Some laptops have a FN key to switch the wireless adapter off. If a recall from hibernation finds the hardware switch switching the wireless adapter off then It cannot switch it back on automatically. Hence, the need for a re-boot.

Here is a link to the troubleshooting guide:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

When this happens again try the command

> rfkill list

If the result says

soft Blocked: yes - then the wireless adapter is switched by Ubuntu. Try clicking Enable Networking and Enable wireless in the Network Icon menu.

If the result says

Hard Blocked: yes - then it is switched off in hardware.

Regards.

---

### Post by varunendra on 2012-03-12
Hi joecmp, Welcome to the forums!

It seems to be a known [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769092"). See if the workaround mentioned this post can help you as it has for many others: [http://ubuntuforums.org/showthread.php?p=11612929](http://ubuntuforums.org/showthread.php?p=11612929)

The linked post suggests only a temporary check. If it works, then a permanent fix is suggested in post #8 by *praseodym* on the same page.

---

