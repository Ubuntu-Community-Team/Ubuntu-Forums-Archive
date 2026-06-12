---
title: "Problem with wireless."
date: 2011-09-29
forum: Hardware
---

### Post by zillen on 2011-09-29
Hello,

I've just installed latest Ubuntu on my Dell Latitude d630 and I doesn't  seem to be able to access the wireless network. Can someone please  assist me?

---

### Post by Tweak42 on 2011-09-30
> **zillen said:**
> Hello,

I've just installed latest Ubuntu on my Dell Latitude d630 and I doesn't  seem to be able to access the wireless network. Can someone please  assist me?

We need to know more about your hardware.  To do this open a terminal and post the output of:

```
lspci
```
and
```
ifconfig
```
and last
```
iwconfig
```

---

### Post by zillen on 2011-09-30
The computer seems to find hardware, but not drivers.

> **Tweak42 said:**
> We need to know more about your hardware.  To do this open a terminal and post the output of:

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

```and
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:17:2e:50  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe17:2e50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7254620 (7.2 MB)  TX bytes:1216998 (1.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```and last
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by Tweak42 on 2011-09-30
```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
```

It was as I suspected, a Broadcom chip.  My D630 has Intel wireless specifically to avoid this problem.  Try the solutions in the sticky thread "Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal)" at the top of the [Networking & Wireless](http://ubuntuforums.org/forumdisplay.php?f=336) forum.

---

### Post by zillen on 2011-10-01
Thanks, but it didn't work for me  thou:(

> **Tweak42 said:**
> ```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
```It was as I suspected, a Broadcom chip.  My D630 has Intel wireless specifically to avoid this problem.  Try the solutions in the sticky thread "Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal)" at the top of the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum.

---

### Post by westie457 on 2011-10-01
Go to _[here]("http://ubuntuforums.org/showpost.php?p=10801185&postcount=240")_ follow the instructions to find the correct drivers and install them.

This has worked for me and a lot of others.

The above assumes you are using 11.04 (Natty). If you are using 10.04 LTS the drivers needed are different

---

