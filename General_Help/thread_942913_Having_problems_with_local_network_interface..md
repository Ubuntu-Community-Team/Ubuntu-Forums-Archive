---
title: "Having problems with local network interface."
date: 2008-10-09
forum: General Help
---

### Post by RheaHS on 2008-10-09
Ok, I have eth1 as my internet connection, and am trying to use eth0 as a local network to my xbox 360 to access live. When I use firstarter, it says eth0 is "not ready". How can I activate it, as I've never had this problem before.

---

### Post by Iowan on 2008-10-09
What's in **/etc/network/interfaces**?  In particular, is there an "auto eth1" line somewhere?

---

### Post by RheaHS on 2008-10-10
All looks normal, just going to look again from the restart I did. 

this is the output now :S It's changed completely. 

auto lo
iface lo inet loopback

---

### Post by Yellow Pasque on 2008-10-10
You can use ifup to bring an interface up.
```
$ ifup --help
Usage: ifup <options> <ifaces...>

Options:
	-h, --help		this help
	-V, --version		copyright and version information
	-a, --all		de/configure all interfaces marked "auto"
	--allow CLASS		ignore non-"allow-CLASS" interfaces
	-i, --interfaces FILE	use FILE for interface definitions
	-n, --no-act		print out what would happen, but don't do it
				(note that this option doesn't disable mappings)
	-v, --verbose		print out what would happen before doing it
	--no-mappings		don't run any mappings
	--force			force de/configuration
```

---

### Post by RheaHS on 2008-10-10
damn, didn't even think of that. Will try it now. 
May start asking for help on the xbox front soon, before the sodding thing takes a flying lesson.

---

### Post by RheaHS on 2008-10-10
Ah. Small problem. Now it's saying that the interface is unknown. This is happening for eth0 and eth1 when inputted with the "ifup" command.

> eth0      Link encap:Ethernet  HWaddr 00:1d:72:02:0f:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1d:d9:52:b7:31  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe52:b731/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20012884 (20.0 MB)  TX bytes:3357807 (3.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209564 (209.5 KB)  TX bytes:209564 (209.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-D9-52-B7-31-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

