---
title: "1394 Networking"
date: 2009-02-15
forum: Hardware
---

### Post by kylehotchkiss on 2009-02-15
i am tying to make an adhoc firewire network. I can't figure out how to get network manager to configure the interface though, just the "ip" command. I would like it to work automatically.

Alright so I have my drivers all loaded and everything, but when I start my computer, I have to "ip addr eth1(firewire) 192.168.0.10 netmask 255.255.255.0 up" and it isn't automatically up like my eth0 (actual Ethernet)

here is my "ifconfig" output:
```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:e2:db:5a  
          inet6 addr: fe80::211:d8ff:fee2:db5a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13686 (13.6 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:19 Base address:0xc800 

eth1      Link encap:UNSPEC  HWaddr 00-11-D8-00-00-2E-2E-23-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

```

[the eth1 doesn't look right for some reason, i meant to ask about that too.]

and here is my "IP" output:
```
:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:11:d8:e2:db:5a brd ff:ff:ff:ff:ff:ff
    inet6 fe80::211:d8ff:fee2:db5a/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ieee1394 00:11:d8:00:00:2e:2e:23 brd ff:ff:ff:ff:ff:ff:ff:ff
4: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 3e:c4:7b:4f:2b:05 brd ff:ff:ff:ff:ff:ff

```
but in there eth1 looks alright?

am I not understanding this?

---

