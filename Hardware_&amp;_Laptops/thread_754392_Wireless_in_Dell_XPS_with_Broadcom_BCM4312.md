---
title: "Wireless in Dell XPS with Broadcom BCM4312"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by bo01 on 2008-04-13
Hi i'd appreciate a little help.

I have followed many HOWTOs but with no success.

I have a Dell XPS 1530. My lspci output is:


```


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)


```

,the lspci -n output

```


00:00.0 0600: 8086:2a00 (rev 0c)
00:01.0 0604: 8086:2a01 (rev 0c)
00:1a.0 0c03: 8086:2834 (rev 02)
00:1a.1 0c03: 8086:2835 (rev 02)
00:1a.7 0c03: 8086:283a (rev 02)
00:1b.0 0403: 8086:284b (rev 02)
00:1c.0 0604: 8086:283f (rev 02)
00:1c.1 0604: 8086:2841 (rev 02)
00:1c.4 0604: 8086:2847 (rev 02)
00:1d.0 0c03: 8086:2830 (rev 02)
00:1d.1 0c03: 8086:2831 (rev 02)
00:1d.2 0c03: 8086:2832 (rev 02)
00:1d.7 0c03: 8086:2836 (rev 02)
00:1e.0 0604: 8086:2448 (rev f2)
00:1f.0 0601: 8086:2815 (rev 02)
00:1f.1 0101: 8086:2850 (rev 02)
00:1f.2 0106: 8086:2829 (rev 02)
00:1f.3 0c05: 8086:283e (rev 02)
01:00.0 0300: 10de:0427 (rev a1)
03:09.0 0c00: 1180:0832 (rev 05)
03:09.1 0805: 1180:0822 (rev 22)
03:09.2 0880: 1180:0843 (rev 12)
03:09.3 0880: 1180:0592 (rev 12)
03:09.4 0880: 1180:0852 (rev 12)
09:00.0 0200: 11ab:4354 (rev 12)
0b:00.0 0280: 14e4:4312 (rev 01)


```

and the ifconfig output:

```


eth0      Link encap:Ethernet  HWaddr 00:15:C5:85:65:4A  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe85:654a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3622880 (3.4 MB)  TX bytes:492744 (481.1 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1F:3A:24:EA:5F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2730 (2.6 KB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

I use the bcm43xx drivers and although i can see the networks i can rarely connect to any of them. I say "rarely" because even if i manage to connect after lots of attempts, after a while i cannot for example visit any site in the browser.

NOTE: The wifi-radar program usually gives me this output:

```


eth1      Interface doesn't support scanning.


```

or its trying to connect (acquiring IP address) and after a while it stops

or (rarely) it connects but actually i have no Internet.

Also, restricted drivers (firmware) are enabled.

Thanks in advance!

---

### Post by bo01 on 2008-04-14
Anyone???

---

### Post by jrharvey on 2008-04-22
I feel your pain. I am having the same problem on my xps 1530

---

### Post by heidricha on 2008-04-23
Hi!

I have just about the same problem.
HP6715b has a bc4312Rev2, but it just does not work under Hardy.

I have tried:
- bcm43xx
- ndiswrapper
- b43
- b43legacy

Tha card can be seen is the lspci:
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

ndiswrapper used to said that "device is present", but nothing worked. 
A pcmcia card with 4318 works fine with b43 module and the recommended fw, it said for the current fw, that it is too new.

There is no even signs of life in dmesg if I only have the buit-in 4312.

---

### Post by heidricha on 2008-04-23
anyway... b43 web page says that 2.6.24 requires a patch for 4312... maybe that's the clue, I mean we should wait for 2.6.25, or newer.

---

