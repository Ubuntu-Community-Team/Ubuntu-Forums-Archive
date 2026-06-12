---
title: "help please! no eth0, modules are loaded &amp; lspci shows eth."
date: 2010-06-13
forum: Hardware
---

### Post by dookiebowser on 2010-06-13
I have no eth0 device after trying to install gentoo. I wiped the drive  and reinstalled ubuntu and still no eth0. 

All I see is loopback adapter. Did my ethernet die? It was working fine  on Ubuntu LiveCD and Ubuntu installed to disk before trying to install  gentoo. The wlan still surprisingly works.

Help please!!!


> $ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:8d:60:a9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe8d:60a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22983554 (22.9 MB)  TX bytes:1406890 (1.4 MB)
> $ lspci -v
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet  Controller
    Subsystem: Intel Corporation Device 0000
    Flags: fast devsel, IRQ 18
    Memory at da000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at 4000 [size=32]
    Capabilities: <access denied>
    Kernel modules: e1000e

> $ lsmod
e1000e                119856  0 This is on a dv6375us HP Pavilion laptop. Ubuntu 10.4 is installed but the same occurred with SystemRescueCD, Gentoo minimal install CD and Ubuntu 10.4 LiveCD.

I have two concerns: 
1. My hard drive gets extremely hot and it is positioned in the notebook right next to the ethernet port and the wifi card. I noticed my wifi is also dropping packets randomly anywhere from 20-50%. So I am stuck with shotty wifi and no wired ethernet. 
Could the heat be causing this much havoc?

2. I notice an error when I boot, somewhere during BIOS checks. The error is
**"PXE-E05: The LAN adapter's configuration is corrupted or has not  been initialized. The Boot Agent cannot continue."**

As far as I know from BIOS configurations, PXE is specific only to booting off of the network...Would this be causing issues??

Thanks in advance.

---

### Post by dookiebowser on 2010-06-14
Still having this issue. 

The ethernet adapter is working properly in Windows 7. It is still not working on Ubuntu LiveCD. 

It used to work perfectly and automnatically before I tried to instlal Gentoo. What could have happened? I've done fresh installs of Ubuntu, tried LiveCD before and after installing Windows 7...no dice.

---

### Post by dookiebowser on 2010-06-15
solved in ABT

[http://ubuntuforums.org/showthread.php?t=1508612](http://ubuntuforums.org/showthread.php?t=1508612)

---

