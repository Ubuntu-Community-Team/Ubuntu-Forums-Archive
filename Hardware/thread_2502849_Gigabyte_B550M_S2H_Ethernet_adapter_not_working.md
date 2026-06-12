---
title: "Gigabyte B550M S2H Ethernet adapter not working"
date: 2024-12-02
forum: Hardware
---

### Post by mar.ste on 2024-12-02
[FONT=monospace][COLOR=#000000]If I plug the cable the system sees it:
[/COLOR][/FONT][FONT=monospace][COLOR=#18b218][ 8690.861361] [/COLOR][COLOR=#b26818]r8169 0000:04:00.0 enp4s0: [/COLOR][COLOR=#000000]Link is Down [/COLOR]
[COLOR=#18b218][ 8702.078593] [/COLOR][COLOR=#b26818]r8169 0000:04:00.0 enp4s0: [/COLOR][COLOR=#000000]Link is Up - 1Gbps/Full - flow control rx/tx[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]
But no address is given by the router:
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]$ ip a [/COLOR]
1: [COLOR=#54ffff]**lo: **[/COLOR][COLOR=#000000]<LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000 [/COLOR]
    link/loopback [COLOR=#ffff54]**00:00:00:00:00:00**[/COLOR][COLOR=#000000] brd [/COLOR][COLOR=#ffff54]**00:00:00:00:00:00**[/COLOR][COLOR=#000000] [/COLOR]
    inet [COLOR=#ff54ff]**127.0.0.1**[/COLOR][COLOR=#000000]/8 scope host lo [/COLOR]
       valid_lft forever preferred_lft forever 
    inet6 [COLOR=#5454ff]**::1**[/COLOR][COLOR=#000000]/128 scope host noprefixroute  [/COLOR]
       valid_lft forever preferred_lft forever 
2: [COLOR=#54ffff]**enp4s0: **[/COLOR][COLOR=#000000]<BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state [/COLOR][COLOR=#54ff54]**UP **[/COLOR][COLOR=#000000]group default qlen 1000 [/COLOR]
    link/ether [COLOR=#ffff54]**b4:2e:99:ec:c0:12**[/COLOR][COLOR=#000000] brd [/COLOR][COLOR=#ffff54]**ff:ff:ff:ff:ff:ff**[/COLOR][COLOR=#000000] [/COLOR]
3: [COLOR=#54ffff]**wlx000e2ebc5baa: **[/COLOR][COLOR=#000000]<BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state [/COLOR][COLOR=#54ff54]**UP **[/COLOR][COLOR=#000000]group default qlen 1000 [/COLOR]
    link/ether [COLOR=#ffff54]**00:0e:2e:bc:5b:aa**[/COLOR][COLOR=#000000] brd [/COLOR][COLOR=#ffff54]**ff:ff:ff:ff:ff:ff**[/COLOR][COLOR=#000000] [/COLOR]
    inet [COLOR=#ff54ff]**192.168.1.115**[/COLOR][COLOR=#000000]/24 brd [/COLOR][COLOR=#ff54ff]**192.168.1.255 **[/COLOR][COLOR=#000000]scope global dynamic noprefixroute wlx000e2ebc5baa [/COLOR]
       valid_lft 85214sec preferred_lft 85214sec 
    inet6 [COLOR=#5454ff]**fdc2:7ccc:39f:c000:8530:5979:de1b:dbb3**[/COLOR][COLOR=#000000]/64 scope global temporary dynamic  [/COLOR]
       valid_lft 7036sec preferred_lft 3436sec 
    inet6 [COLOR=#5454ff]**fdc2:7ccc:39f:c000:72e9:9e38:942d:dd2d**[/COLOR][COLOR=#000000]/64 scope global dynamic mngtmpaddr noprefixroute  [/COLOR]
       valid_lft 7036sec preferred_lft 3436sec 
    inet6 [COLOR=#5454ff]**fe80::ebbf:493d:ff47:ab9b**[/COLOR][COLOR=#000000]/64 scope link noprefixroute  [/COLOR]
       valid_lft forever preferred_lft forever 
4: [COLOR=#54ffff]**docker0: **[/COLOR][COLOR=#000000]<NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state [/COLOR][COLOR=#ff5454]**DOWN **[/COLOR][COLOR=#000000]group default  [/COLOR]
    link/ether [COLOR=#ffff54]**02:42:6c:6d:96:96**[/COLOR][COLOR=#000000] brd [/COLOR][COLOR=#ffff54]**ff:ff:ff:ff:ff:ff**[/COLOR][COLOR=#000000] [/COLOR]
    inet [COLOR=#ff54ff]**172.17.0.1**[/COLOR][COLOR=#000000]/16 brd [/COLOR][COLOR=#ff54ff]**172.17.255.255 **[/COLOR][COLOR=#000000]scope global docker0 [/COLOR]
       valid_lft forever preferred_lft forever

[/FONT][FONT=monospace][COLOR=#000000]$ sudo lshw -c network [/COLOR]
  *-network                  
       description: Ethernet interface 
       product: RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: enp4s0 
       version: 16 
       serial: b4:2e:99:ec:c0:12 
       size: 1Gbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.11.0-9-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=yes multicast=yes port=twisted pair spe
ed=1Gbit/s 
       resources: irq:33 ioport:e000(size=256) memory:fcc04000-fcc04fff memory:fcc00000-fcc03fff

I tried many times to restart the system and even trying some changes on the router with no success. The wired RaspBerry 5 on the side is instead working properly.

[/FONT]
For information, looking for solutions I've seen on internet a similar problem (with no answer anyway): [https://askubuntu.com/questions/1530739/ethernet-not-working-on-ubuntu-realtekrtl8111-8168-8411-works-fine-on-windows](https://askubuntu.com/questions/1530739/ethernet-not-working-on-ubuntu-realtekrtl8111-8168-8411-works-fine-on-windows)

---

### Post by TheFu on 2024-12-04
How much is your time worth dealing with poor quality ethernet chips?  The B550 usually has 2.5Gbps ethernet, so perhaps using the correct driver would be the first thing to try?  I don't know about Gigabyte B550 motherboards.  Gigabyte is Linux-hostile. Once I realized that, I stopped giving them money.

Or you could set a static IP  .... or spend $25 for an Intel NIC and be done with it.

---

### Post by him610 on 2024-12-05
FWIW: While doing some research on AM4 systems, I discovered AsRock B550 has intel chips

---

### Post by TheFu on 2024-12-06
> **him610 said:**
> FWIW: While doing some research on AM4 systems, I discovered AsRock B550 has intel chips

The hardware report above says it has a Realtek 8111H GigE NIC.  

There are multiple models of AsRock B550M motherboards.  I know that the Asus B550 Gaming uses an Intel i211 NIC, but Asus is NOT the same as AsRock.  [https://pcpartpicker.com/products/compare/nFhmP6,NT7p99,LKLwrH,G6VG3C/](https://pcpartpicker.com/products/compare/nFhmP6,NT7p99,LKLwrH,G6VG3C/) shows all of them use Realtek NICs. Some are 2.5Gbps and some are 1 Gbps.  

I filtered based on _AsRock_ and _B550M_. None use anything except Realtek wired NICs in that filter.  Too bad pcpartpicker doesn't allow actually filtering on NIC vendor.  Of course, pcpartpicker data can be flawed.

---

