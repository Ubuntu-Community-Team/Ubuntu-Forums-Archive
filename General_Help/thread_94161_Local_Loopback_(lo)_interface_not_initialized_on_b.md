---
title: "Local Loopback (lo) interface not initialized on boot"
date: 2005-11-23
forum: General Help
---

### Post by aminalshmu on 2005-11-23
All in the topic. When I boot I get this:

```
jordan@jordan:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:48:0C:8C:21
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:48ff:fe0c:8c21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1962356 (1.8 MiB)  TX bytes:129839 (126.7 KiB)
          Interrupt:21 Base address:0xa000
```

i have to do "ifconfig lo 127.0.0.1" before i can log in to gnome, use "sudo", connect to MPD, etc. but my outbound internet works just fine. can anyone tell me how i can get "lo" to be configured properly on boot? and maybe how i could have possibly screwed this up? :p

---

### Post by gapplewagen on 2005-11-23
Look in the file /etc/network/interfaces

Near the top do you have:

```

auto lo
iface lo inet loopback

```
?

---

### Post by aminalshmu on 2005-11-23
a-ha. i was missing the "auto lo" line. wonder why it disappeared...? curious. thanks a lot.

---

### Post by gapplewagen on 2005-11-24
Did you upgrade anything recently?

---

### Post by aminalshmu on 2005-11-24
compiled and running new kernel (2.6.14.2 vanilla)... don't know how that would change my network interfaces file though...

---

