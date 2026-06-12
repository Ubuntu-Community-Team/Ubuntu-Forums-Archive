---
title: "Sis900 Network card problem"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by deep75 on 2008-04-15
I'm trying to install Ubuntu Gutsy on an old and buggy laptop of a friend. The problem is that the dvd is broken. But I have an old laptop with similar hardware (PIII 800 sis based), so I put the hard disk of my friend's pc on my laptop and I install Ubuntu, then I put back the disk on the other pc :)

Everything works fine except of the network (on my old pc the net cip was different). The card is a sis900
```
ricky@xtrema:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 11)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 80)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 01)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:03.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 11)

```

```
ricky@xtrema:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       logical name: eth0
       version: 80
       serial: 00:a0:cc:c5:f5:11
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half ip=192.168.1.3 latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s

```

and the module is loaded

```
 ricky@xtrema:~$ lsmod | grep sis900
sis900                 24960  0 
mii                     6528  1 sis900

```

and the card is working

```
ricky@xtrema:~$ sudo ethtool -i eth0
driver: sis900
version: v1.08.10 Apr. 2 2006
firmware-version: 
bus-info: 0000:00:01.1
```

```
ricky@xtrema:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:C5:F5:11  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164416 (160.5 KB)  TX bytes:164416 (160.5 KB)
```

The problem is with dmesg

```
ricky@xtrema:~$ dmesg | grep eth
[   24.819663] eth0: SiS 900 PCI Fast Ethernet at 0xd000, IRQ 11, 00:a0:cc:c5:f5:11.
[   43.883098] eth0: Media Link Off
[   45.661370] ADDRCONF(NETDEV_UP): eth0: link is not ready
```


When I plug the cable the corrisponding light on the router is blinking and I can't ping the net.

I boot with acpi=off in grub.conf but nothing change, and I try to change the cable but no effect ](*,)

Any suggest?

Thank's

---

### Post by Bateman on 2008-04-26
I think I have exactly the same problem. The card works fine under Windows and it's worked with other Linux distributions before. I'm sure it even worked with Ubuntu live cds before. It's recognised, as deep75 says, and it goes through the motions of connecting but the network manager icon just spins and spins after the first green light comes on. I've tried changing cables, manual configuration, restarting everything, editing /etc/hosts and etc/network/interfaces, adding acpi=noirq and apm=off to /boot/grub/menu.lst etc etc but nothing works. I have the output of all of those commands saved but I don't want to hijack your thread. Let me know if they'd be useful. I do think we have exactly the same problem though so it's perhaps best if I post here too. Can anyone help?

---

### Post by Bateman on 2008-04-26
Shouldn't this thread really be in the Networking forum? After all the card *is* detected. Can someone move it?

---

