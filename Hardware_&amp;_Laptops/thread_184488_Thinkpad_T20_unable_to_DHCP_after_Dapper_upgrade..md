---
title: "Thinkpad T20 unable to DHCP after Dapper upgrade."
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by rudyard on 2006-05-30
Hi Folks, had Breezy for 5 seconds then Dapper came out, still learning the interface (Mac and PC background).  Nice thing is both my soundcard and ethernet card now work, though the wireless showed as disconnected. I'm staying in a place that has an open system. Went home to my system, changed it to Manual DHCP, it connected, then back to DHCP. Worked fine. Came back to the place I'm 'sitting, can't connect, even using that trick. 

Not use to not being able to see other broadcast points so as to choose the one you want to connect to.

Anyway ifconfig -v gives:

(wireless)
eth0      Link encap:Ethernet  HWaddr 00:etc etc
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

(ethernet card)
eth1      Link encap:Ethernet  HWaddr 00:etc etc
          inet addr:192.168.2.xxx  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:86ff:etc etc Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9008 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:28333063 (27.0 MiB)  TX bytes:630769 (615.9 KiB)
          Interrupt:11 Base address:0x8400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/xxx Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2227036 (2.1 MiB)  TX bytes:2227036 (2.1 MiB)

Any thoughts? Thanks

-Rudyard

---

