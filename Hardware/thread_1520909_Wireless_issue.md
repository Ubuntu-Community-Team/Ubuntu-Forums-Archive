---
title: "Wireless issue"
date: 2010-06-30
forum: Hardware
---

### Post by spikoley on 2010-06-30
I have a strange wireless issue where the device is not found.  The wireless card is seen in *lspci*, but when I run *ifconfig eth1 up* it is not found.  In the past the solution was to shut down and boot into Windows.  When I booted back into Ubuntu it would work.  I don't run Windows any more, so that isn't a solution.  It happens in two installs of Ubuntu on the same laptop.  It effects my PCMCIA card too.  The PCMCIA card works fine in another laptop.  I do not think this is card related.  I believe it has something to do with the hardware not being "released".  The card worked fine before.  

Any ideas?  

> ERROR while getting interface flags: No such device

```
Network controller: Intel Corporation PRO/Wireless LAN 2100 Mini PCI Adapter (rev 04)
```

Trouble Shooting Step

1.  Rebooted
2.  Shut down
3.  Booted into different Ubuntu intall
4.  Turned off wireless in the BIOS, halted, booted, turned on in the BIOS and booted
5.  Ran ifconfig up and down
6.  Ran /etc/init.d/networking restart, stop, start and force-reload
7.  Removed the batter and power
8.  Ran iwconfig eth1 mode managed, monitor and master

What else should I try?

---

### Post by spikoley on 2010-07-02
I found some errors in /var/log/dmesg.

> ipw2100: eth1: Firmware 'ipw2100-1/3.fw' not available or load failed
ipw2100: eth1: ipw2100_get_firmware failed -2
ipw2100: eth1: Failed to power on the adapter.
ipw2100: eth1: Failed to start the firmware.

lsmod grep ipw
> 
ipw2100		69768	0
libipw		26712	1
lob80211	 5176	1


Any ideas on what to do?  It looks like an issue with the firmware and the hardware cannot be turned on.  In the past I would fix this issue by booting into Windows, but I that is not an option because I do not run Windows anymore.

---

### Post by spikoley on 2010-07-03
Here are some more details.

lshw -C

> *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:26:4e:98
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.98 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=34 mingnt=2

---

