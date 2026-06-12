---
title: "Toshiba satellite L650 -181 with 12.04 problems~"
date: 2012-05-11
forum: Hardware
---

### Post by nimirooyn on 2012-05-11
I have been working with linux for sometime and never ran into this kind of problems :\
my Eth0 is for some reason "not managed" O_O tried to reinstall it, got into gedit and wrote it in manually(including loopback ofc)
still nothing... wireless works perfectly but wired doesn't.

another thing that happend since transfered from 11.10 to 12.04 is that my sound card doesn't want to recognize itself... it worked only on the built in, didn't even recognize the type... and when connected through hdmi to other monitor(32" samsong with full hd) didn't transfer sound and didn't recognize it as a 32" screen but as a 7" screen o_O
tried to reinstall alsa plugings and such but it did nothing but take up my time...

at the end I have to transfare to windows with dualboot if I want to view hd or to use eth cable....


anyone have any thought as to how to solve it?...


4gb ram, intel hdmi card(base), etheros eth card

ifconfig produced this:
[HTML]
eth0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          inet addr:10.100.102.4  Bcast:10.100.255.255  Mask:255.255.0.0
          inet6 addr: fe80::226:b6ff:fefb:ed7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71338 errors:0 dropped:0 overruns:0 frame:5325
          TX packets:65054 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68297657 (68.2 MB)  TX bytes:9388585 (9.3 MB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          inet addr:169.254.8.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1042954 (1.0 MB)  TX bytes:1042954 (1.0 MB)
(ff:ff:ff:ff:ff:ff for real mac :) )

[/HTML]
ispci produced this : ```


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```

would much ablige any advice anyone get give me ... I'm getting hopeless here... ](*,):cry:

---

