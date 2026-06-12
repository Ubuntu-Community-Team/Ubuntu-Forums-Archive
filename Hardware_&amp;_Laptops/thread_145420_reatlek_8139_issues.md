---
title: "reatlek 8139 issues"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by woodmeister on 2006-03-16
I've been using breezy for several months with no problems, then yesterday i changed my router, and now i can't get a network connection.

I have green lights on the board itself and the connection is fine on windows xp

mii-tool eth0 gives invalid argument

lspci l grep Eth lists my card as a rtl 8139, which is correct
lspci l grep mii gives:-
mii        5696       2   8139c,8139too

the card does not come up on ifconfig, and route -n gives an emtpy table.

I'm thinking this could be a problem with 8139c,8139too both being loaded, but why this has suddenly happened now i have no idea.
All in all im very confused, any help appreciated.

mark

---

### Post by Ensnared on 2006-03-16
What happens if you run "ifup eth0"?
Does it show up under "ifconfig -a"?

My guess is your new router doesn't give you an IP-address from DHCP, so you'll need to configure it's (presumably built-in) DHCP-server, or you can set your card up with a static IP.

---

### Post by woodmeister on 2006-03-16
This is what i get from ifup and ifconfig -a
Windows xp and another ubuntu box are getting given dhcp adresses without any problem.

wood@wood1:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:10:dc:c7:a0:32
Sending on   LPF/eth0/00:10:dc:c7:a0:32
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down

wood@wood1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:DC:C7:A0:32
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:108192 (105.6 KiB)  TX bytes:108192 (105.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Ensnared on 2006-03-16
Yeah, if other machines are getting IP's normally then the DHCP-server isn't the problem :) It seems like it's trying to get an address though, but the ifconfig-output shows that it's not sending or receiving any data at all (both RX and TX packets are 0).

You didn't do any changes at all to your box at the same time as the problem started? It really does seem like a driver-problem, but that doesn't make much sense if nothing's been changed. Linux shouldn't care if there's suddenly a different hardware-box on the network or not.

Do you still have your old router? If you do, try switching back to it just to see if it works then. It shouldn't make any difference, but I've been around too long to say anything definite without having it tested first ;) If your doing this means it works, chances are your new router just needs a firmware upgrade as it may be some kind of compatibility-issue with specific hardware. That doesn't make much sense logically, but it's worth a shot.

Coincidentally I'm having problems with an adapter with the same chip myself (rtl8139), but I suspect mine's simply got a busted port since it transmits packets but doesn't receive any. It could be that the driver isn't entirely stable though - I wouldn't know since I only have one box with that chip, and 3Com on all the others.

---

### Post by woodmeister on 2006-03-17
Ok, I get exactly the same results with my old router now. On the day I changed the router I also got the latest security updates through adept (the kde frontend to apt). So I'm thinking that this must have messed up the driver in some way. I'm still not happy about both 8139too and 8139cp being loaded, I've no idea if this was the case before though. Anyone got ideas how to solve this other than a reinstall?

---

### Post by rlklee on 2006-03-20
I should add that I have this exact same problem, which started, as well, with recent security updates.  Any new info on this?

---

### Post by manfredfr on 2006-03-21
Welcome in the world without network. I got similar issues see thread: [http://ubuntuforums.org/showthread.php?t=146846]("http://ubuntuforums.org/showthread.php?t=146846")
I created a bug report as well but this seems to be useless. 

let you know if I hear something.

Cheers

---

### Post by Titus A Duxass on 2006-03-21
This may or may not work but try it.

Shutdown but do not disconnect from mains (don't pull plug).
Remove Wireless card.
Restart
Shutdown but do not disconnect from mains (don't pull plug).
Reinstall Wireless card.
Restart.

I have similar problems and this is my cure.

No guarantees

---

### Post by manfredfr on 2006-03-21
In my case the problem was acpi related - just try to boot with boot option 
> pci=noacpi

---

