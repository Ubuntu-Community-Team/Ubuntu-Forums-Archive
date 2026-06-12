---
title: "Wired Network not working (Intel(R) PRO/1000 Network Driver)"
date: 2009-12-18
forum: Hardware
---

### Post by nicolasdiogo on 2009-12-18
hello folks,

i am having problems with my wired network.

it is a T61p laptop from lenovo that i have used ubuntu since version 7 x64.
And this is the first time i find that my wired network does not work.

interisting enough my wireless is flawless.

the dmesg gives me the following output:
```

$ cat laptop_dmesg.txt | grep e1000
[    2.149780] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    2.149783] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.149887] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.149895] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[    2.149905] e1000e 0000:00:19.0: setting latency timer to 64
[    2.150160] e1000e 0000:00:19.0: irq 31 for MSI/MSI-X
[   18.272945] e1000e 0000:00:19.0: irq 31 for MSI/MSI-X
[   18.332816] e1000e 0000:00:19.0: irq 31 for MSI/MSI-X

```

dmesg is attached.

i have also noticed that my network lights (close to the network socket) are always on. and i am quite sure that they have not been on with previous versions.

i checked and the required modules is correctly loaded:
```

$ lsmod | grep e1000
e1000e                138672  0 

```

has anyone else had this problem before?
any suggestions on how to fix it?

many thanks,

Nicolas

---

### Post by michael-wd21 on 2009-12-18
There's nothing in what you've provided that indicates a problem. Please can you provide the output of

```
 ifconfig -a 
```

and

```
 netstat -rn 
```

Thanks.

Michael

---

### Post by nicolasdiogo on 2009-12-18
thanks Michael,

here are the results:
```

# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:12:56:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1c:25:12:56:97  
          inet addr:169.254.5.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24796 (24.7 KB)  TX bytes:24796 (24.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:b8:17:27  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:feb8:1727/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5755219 (5.7 MB)  TX bytes:1535151 (1.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-B8-17-27-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and

```

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```

looking forward to your suggestions.

---

### Post by nicolasdiogo on 2009-12-18
would it not be a problem the line below on dmesg?

[B][    2.149895] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[/B]

---

### Post by michael-wd21 on 2009-12-18
Have you disabled your wireless before attempting to connect via wired? It looks like your wireless was enabled when you produced that output. Please disable wireless, attempt to establish wired connectivity then capture ```
ifconfig -a
``` and ```
netstat -rn 
``` output.

I don't think the **pci_enable_pcie_error_reporting** message is necessarily an issue, the module is loaded and the interface is listed but it's just not got a valid IP configuration.

---

### Post by nicolasdiogo on 2009-12-18
hi,

i turned wifi off and re-done the tests:
```


# dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 3124
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1c:25:12:56:97
Sending on   LPF/eth0/00:1c:25:12:56:97
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:12:56:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1c:25:12:56:97  
          inet addr:169.254.5.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39268 (39.2 KB)  TX bytes:39268 (39.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:b8:17:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:35456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29585515 (29.5 MB)  TX bytes:5405180 (5.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-B8-17-27-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


```


i have also checked if the DHCP SERVER is working correctly (it is a router) and plugged my other windows laptop - the network picks up fast and assigns a valid IP.

thanks

---

### Post by michael-wd21 on 2009-12-18
I don't see any problems with what you're doing, I would now normally think there must be a cable fault or something, but that eth0:avahi interface is not familiar to me. So I looked it up and found this web page:

[http://omingo.zorngrid.com/](http://omingo.zorngrid.com/)

Maybe you could have a look at that? I'm afraid I've never seen eth0:avahi on any of my boxes Ubuntu or Debian, so I don't know if it'll help or not!

Please let us know if it does. Maybe someone who knows this avahi stuff will jump in?

Michael

---

### Post by nicolasdiogo on 2009-12-18
thanks for the suggestions but it did not work.

if can not fix this i will have to downgrade!!

this is a show stopper.


thanks,

Nicolas

---

### Post by jaskah on 2010-01-12
hello

i was just wondering if you found a solution to your problem. i have a lenovo t61 and am experiencing -- quite suddenly -- similar problems connecting to my wired network.

like you, both lights by the ethernet port -- the yellow and green light -- are always on.

i am running ubuntu 9.04.

any help will be greatly appreciated.

thanks.

jason

---

### Post by nicolasdiogo on 2010-01-13
hi,

i installed 9.10 x64 which gave problems and to solve it i downgraded to 9.04 x64.

it works fine on my machine.

have you tried deleting UDEV network rules and rebooting the machine.

i am not running linux now, but it is under /etc/udev/7*-networking/some-file

open this file to find if it is the one that sets up the network card.

ADDITIONALLY, do have bridge connection on this laptop? do you use virtual machines such as Xen or KVN?

hope it helps.

Nicolas

---

### Post by jaskah on 2010-01-13
hi nicolas

thanks for your reply. i managed to get it working again by following all the links above but, to tell you the truth, i still don't know what the actual problem was or how i managed to fix it.

i've been running 9.04 since it was released but this is the first time i've had this particular problem occur on my computer.

with best regards

jason

---

