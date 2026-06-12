---
title: "liksys USB200M network adapter problems"
date: 2008-04-23
forum: Hardware
---

### Post by lateralus01 on 2008-04-23
I have a linksys USB200M fast ethernet adapter and I just can't seem to get it to work.  I looked on the web and the modules I found are usbnet and axnet-cs.  I built both of them as modules in the kernel.
then I ran:

modprobe usbnet
modprobe axnet_cs

they both worked fine without any errors and i checked and the adapter is detected:
```

Master ~ # lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 002: ID 045e:0288 Microsoft Corp. Xbox Controller S Hub
Bus 001 Device 005: ID 045e:0289 Microsoft Corp. Xbox Controller S
Bus 001 Device 006: ID 13b1:0018 Linksys USB200M 10/100 Ethernet Adapter

```

but nothing is shown when I run ifconfig:
```

Master ~ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:3A:BF:6B:B4
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:3aff:febf:6bb4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:318973 (311.4 Kb)  TX bytes:158037 (154.3 Kb)
          Interrupt:4 Base address:0x5000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

There should be an interface called usb0 but it's obviously not there.

What should I do?

Thanks,
Lateralus01

---

