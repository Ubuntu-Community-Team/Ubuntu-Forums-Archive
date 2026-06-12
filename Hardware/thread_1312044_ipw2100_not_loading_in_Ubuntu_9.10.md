---
title: "ipw2100 not loading in Ubuntu 9.10"
date: 2009-11-02
forum: Hardware
---

### Post by gmerrick on 2009-11-02
I have a toshiba Tecra S1 laptop with an Intel 2100/3b wireless card.  under 8.04 and 8.10 I had it working and the lastest upgrade to 9.10 disabled it.

I then proceeded to do a complete clean install with the release version of 9.10 to no avail.

doing a lshw -C network I get:
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=34 mingnt=2
       resources: memory:d0001000-d0001fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:a0:d1:45:2b:bf
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.146 latency=128 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s resources: irq:6 memory:d0000000-d0000fff 
ioport:a080(size=64)

------

The ipw2100 driver exists as I can find it on the system however when I do a 

merrick@tipvigut:~$ sudo modinfo ipw2100
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        git-1.2.2
description:    Intel(R) PRO/Wireless 2100 Network Driver
srcversion:     8C79E1425302034B3D80689
alias:          pci:v00008086d00001043sv00008086sd000025A0bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002598bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002596bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002593bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002591bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002592bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002590bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002587bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002586bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002585bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002581bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002583bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002582bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002580bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002570bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002567bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002566bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002565bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002561bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002563bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002562bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002560bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002555bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002554bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002553bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002551bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002550bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Dbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Cbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Bbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002529bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002528bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002527bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002523bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002522bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002526bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002525bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002524bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002521bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002520bc*sc*i*
depends:        libipw
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
parm:           debug:debug level (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           channel:channel (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)

I show that the driver is at least available for the system to use.  When doing a sudo modprobe ipw2100 there are no complaints, but nor is there any action on the networking side either.

I have tried to restart the networking modules with sudo /etc/init.d/networks restart but nothing happens there either.

Any suggestions?

---

### Post by visicon on 2009-12-28
Has anyone found a solution to this problem? I'm have the exact same problem.

  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=34 mingnt=2
       resources: memory:d0001000-d0001fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:a0:d1:d8:40:13
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.123.18 latency=128 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:6 memory:d0000000-d0000fff ioport:a080(size=64)

santo@ubuntu-laptop:~$ sudo modinfo ipw2100
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        git-1.2.2
description:    Intel(R) PRO/Wireless 2100 Network Driver
srcversion:     8C79E1425302034B3D80689
alias:          pci:v00008086d00001043sv00008086sd000025A0bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002598bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002596bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002593bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002591bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002592bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002590bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002587bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002586bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002585bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002581bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002583bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002582bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002580bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002570bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002567bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002566bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002565bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002561bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002563bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002562bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002560bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002555bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002554bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002553bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002551bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002550bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Dbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Cbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Bbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002529bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002528bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002527bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002523bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002522bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002526bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002525bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002524bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002521bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002520bc*sc*i*
depends:        libipw
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
parm:           debug:debug level (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           channel:channel (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)

Has anyone found a solution or can offer a suggestion?

Thanks

---

