---
title: "Prolink PHS100 + acer aspire one D250 UNR"
date: 2009-10-26
forum: Hardware
---

### Post by suomaf on 2009-10-26
Hey all,

I have got the modem all configured and working. Today though when I plugged in a eth0 line and the modem seem to have lost the dns. I am able to ping 202.162.22.222 fine but I cannot ping google.com
Anything with just ips can be reached but anything with just name cannot be reached. Is there any thing I can check?

OS Jaunty netbook remix
modem prolink phs100

I dial using wvdial.

Thanks guys

---

### Post by suomaf on 2009-10-26
This is bizarre. It is working now. I suspect that the ISP's dns was not working.
This is my route ouput
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

```
and this is my ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:26:22:5a:bf:f8  
          inet6 addr: fe80::226:22ff:fe5a:bff8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5388 errors:0 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000 
          RX bytes:3323026 (3.3 MB)  TX bytes:937805 (937.8 KB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22232 (22.2 KB)  TX bytes:22232 (22.2 KB)

pan0      Link encap:Ethernet  HWaddr aa:d7:6e:ff:fd:fa  
          inet6 addr: fe80::a8d7:6eff:feff:fdfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:123.231.60.198  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1062374 (1.0 MB)  TX bytes:84249 (84.2 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:62:ba:2b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 0C-60-76-62-BA-2B-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

The question I guess is, Is there anyway to get wvdial to use static dns instead of the ones that is assigned by the ISP. I know that there are solutions floating around but it seems to be with previous version of ubuntu.

Appreciate if anyone can help. Thanks

---

### Post by suomaf on 2009-10-27
Can anyone help me please? I think the problem is with the DNS. I need to know how to configure the dns after wvdial has connected.

Thanks

---

