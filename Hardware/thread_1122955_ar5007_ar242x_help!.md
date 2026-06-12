---
title: "ar5007 ar242x help!"
date: 2009-04-11
forum: Hardware
---

### Post by fifteenrabbits on 2009-04-11
Alright. I had this working for some time without any trouble. Then synaptic updated something and when I restarted, no more wifi.

Under the stock network manager, it shows my wired networks, and then, under the heading "wireless networks" there is nothing. Also, when I try to hook up to my network using the "connect to hidden network" tool, it just tries to connect for a while before giving up.

Here are some infos that might be useful:

uname -a Output:

Linux evan-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux


iwconfig Output:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist scanning output:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

sudo lshw -C network Output:
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:9d:12:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:d2:03:74:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:b8:25:30:4e:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Please help. I've got stuff to do! :)

-Fifteen Rabbits

---

### Post by fifteenrabbits on 2009-04-11
Oh come on! I know this might seem like well-worn territory but I've tried everything I've found!

Pleeeeease help!

---

### Post by fifteenrabbits on 2009-04-12
Alright! Issue solved (sort of).

At any rate, it was a hardware issue. The hardware wouldn't work when I booted into windows, either.

I rebooted a bunch of times. Turned the wifi switch off and on a number of times. Booted with it off, and then turned it on, and voila, it worked.

This is the second time this has happened, but it was not for nearly as long last time. If anybody has any idea for a repair or fix, I'd appreciate it.

Thanks,
Fifteen Rabbits

---

