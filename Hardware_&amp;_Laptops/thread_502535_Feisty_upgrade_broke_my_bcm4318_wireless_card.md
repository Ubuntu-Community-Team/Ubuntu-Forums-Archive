---
title: "Feisty upgrade broke my bcm4318 wireless card"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by otakuj462 on 2007-07-16
Hello, I just upgraded from Edgy to Feisty on my Dell Inspiron 1300. I've been using ndiswrapper with the bcm4318 wireless card, and it was working fine before the upgrade. Now, however, ndiswrapper is exhibiting very strange behaviour. 

```
jacob@jacob-laptop:~$ sudo ndiswrapper -i bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

```

```
jacob@jacob-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5a         driver installed, hardware present

```

```

jacob@jacob-laptop:~$sudo modprobe ndiswrapper
jacob@jacob-laptop:~$dmesg
[...]
[100136.672000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[100136.712000] usbcore: registered new interface driver ndiswrapper


jacob@jacob-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:A9:6C:29
          inet addr:192.168.15.104  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fea9:6c29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8566787 (8.1 MiB)  TX bytes:779152 (760.8 KiB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:689455 (673.2 KiB)  TX bytes:689455 (673.2 KiB)

```

There appears to be nothing I can do to get eth1 to show up in ifconfig. And yet, modprobing ndiswrapper does not cause any errors to appear in dmesg.
If anyone has any advice, I would greatly appreciate it if you would let me know.
Thanks.

Jake

---

