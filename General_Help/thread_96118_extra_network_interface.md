---
title: "extra network interface"
date: 2005-11-28
forum: General Help
---

### Post by bassMonkey on 2005-11-28
Hi,
I recently noticed that a new network interface had appeared from nowhere(?), I only have one nic but both eth0 and eth1 seem to exist. eth1 doesn't have an ip and some error is reported during boot but I can't read it fast enough. 

> 
bassserver:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:55:D6:EC
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe55:d6ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31177364 (29.7 MiB)  TX bytes:3350342 (3.1 MiB)
          Interrupt:5 Base address:0xc000

bassserver:~# ifconfig eth1
eth1      Link encap:UNSPEC  HWaddr 00-02-3C-00-81-00-B5-A0-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


So why is it there and how can I get rid of it?

---

### Post by wanger123 on 2005-11-28
Are you sure it's not:
eth0=wired ethernet
eth1=wireless ethernet

that's how my Dell laptop is with the broadcom NIC

ciao
wanger

---

### Post by bassMonkey on 2005-11-28
Definitely sure. There's no wlan ;) 
But I'm not sure if firewire could act that way, seen it on winxp, but I don't know why it would be called eth1 in that case and why there'd be an error at boot?

---

