---
title: "Problems with RTL8111/8168B"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by nignasi on 2007-05-09
Hi,
I have problems with ethernet cards. I've 6 PC's with winXP and Ubuntu (Edgy and Feisty). Everything works with WinXP but I ethernet card doesn't work on Ubuntu. In fact sometimes (1%)  it works and somtimes (99%) it doesn't. 
From 'lspci' I know it's a RTL8111/8168B and I think that motherboard is ASUS (I don't know how to know it).
> 
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


I've read some comments about trying 'rmod r8169' and 'modprobe r8169' but not success.

Here you have some other information:

ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:18:F3:F4:67:74  
          inet addr:172.28.1.15  Bcast:172.28.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2572 (2.5 KiB)  TX bytes:2572 (2.5 KiB)


sudo lshw -C network
> 
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:f4:67:74
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=172.28.1.15 latency=0 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:b000-b0ff iomemory:db000000-db000fff irq:17


Could you help me?

Thank you,

Ignasi

---

### Post by bobpaul on 2007-06-19
I found this note on the [Gentoo Wiki article]("http://gentoo-wiki.com/HARDWARE_RTL8168") about this eth that might help you:
> 
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey) 

Perhaps that 1% of the time your ethernet was somehow magically enabled (perhaps by windows crashing and not shutting down properly, thus leaving the adapter enabled).

Good luck! I don't have that hardware, so I can't try it myself...

---

### Post by nignasi on 2007-06-20
Thank you very much for this information.
I will try.

Ignasi

---

### Post by inferno0069 on 2007-06-29
> **bobpaul said:**
> I found this note on the [Gentoo Wiki article]("http://gentoo-wiki.com/HARDWARE_RTL8168") about this eth that might help you:


Perhaps that 1% of the time your ethernet was somehow magically enabled (perhaps by windows crashing and not shutting down properly, thus leaving the adapter enabled).

Good luck! I don't have that hardware, so I can't try it myself...

Thanks! It worked for me.

---

