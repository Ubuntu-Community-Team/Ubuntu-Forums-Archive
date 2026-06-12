---
title: "Installed Kubuntu, no more Internet"
date: 2005-11-05
forum: General Help
---

### Post by jobi21 on 2005-11-05
Hi

Just finished installing Kubuntu on an IBM T42p and I can't get networking to work. It has two nic's; eth0 using e1000, and a wireless which shows up as eth1 - using ipw2100.

I am unable to get an DHCP address from my router (Zyxel ZyAIR B-2000 v.2) and if I try to set an static address I am unable to ping the gw.

I've tried disabling IPv6, but to no avail.

Furthermore, when I tried to get an address via the wireless adapter it actually fried my router. It stopped working and I had to unplug the power.

What is going on?! The hardware in question worked flawlessly when running Gentoo ;)

---

### Post by kairu0 on 2005-11-05
First of all, the gui networking tools are screwed up in Kubuntu Breezy. To get my network working, I had to do it from the command line.

First, are you sure that Kubuntu has found your wireless card? Check with "ifconfig" and see if there's a eth1 entry. If there isn't, you may need ndiswrapper.

Second, look at /etc/network/interface. You should have two auto lines (auto eth0, auto eth1) Make sure that they are in that order.

Good luck!

---

### Post by Inspector Hector on 2005-11-05
Same Problems here. Just installed Kubuntu again, after giving openSuSE 10 a try. I was unable to set my network cards up correctly. 

I have two normal ethernet cards and one wireless. The network tools didn't let me to enable any of these. Any time i changed the gw, the tools didn't remembered the ip and the specified device. 

I tried 3 hours to understand how to change the gw with "route" manually, but i failed. The i typed in "sudo dhclient" (don't ask me why :), and the route, and dns i think, was set up correctly.

Funniest bug is, that i can't go into the network tools now, because anytime i want to go in "Administrator Mode" it switches back without letting me change something. It tells me that i have to click the admin button :-)

I'am really having fun with Kubuntu ](*,)

Btw, i had to restart my router 5 or 6 times i guess. I would be really happy if someone could tell, why this is gonna happen to me, an how i can defeat

... argh, even now the the connection is not stable ...

---

### Post by kairu0 on 2005-11-05
[QUOTE=Inspector Hector]
Funniest bug is, that i can't go into the network tools now, because anytime i want to go in "Administrator Mode" it switches back without letting me change something. It tells me that i have to click the admin button :-)
[/QUOTE]

This is a well-known bug...and it's drawn me closer to my friend Mr. Command Line. :P

---

### Post by Inspector Hector on 2005-11-06
But why is it so unstable, even when i'am using the command line? It's like a heartbeat, send it, send nothing, send it, send nothing. 

My only idea is, that dhclient doesn't configured everything right. So this would be the next question. 

What configuration should be set, and where can i see and modify it, when i'am using my router as a dhcp-server with 192.168.1.1, and my laptop (and all the other computers), are getting ips from ...100 to ...200?

ifconfig shows me, that my cards are set up correctly. 
route shows me, after using dhclient, a default->router route

What have i forgotten?

And i'am not using my wireless card, to reduce potential sources of errors.

---

### Post by Inspector Hector on 2005-11-06
Some details, maybe help helping me

route gives me ```

Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         netgear         0.0.0.0         UG    0      0        0 eth0

```
sudo dhclient ```

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth2/00:12:f0:2b:3f:81
Sending on   LPF/eth2/00:12:f0:2b:3f:81
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth1/00:13:77:00:f5:64
Sending on   LPF/eth1/00:13:77:00:f5:64
Listening on LPF/eth0/00:00:f0:95:16:2a
Sending on   LPF/eth0/00:00:f0:95:16:2a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 36640 seconds.

```
ifconfig (only for eth0)
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:00:F0:95:16:2A
          inet Adresse:192.168.1.101  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::200:f0ff:fe95:162a/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22906 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:16592902 (15.8 MiB)  TX bytes:3463411 (3.3 MiB)
          Interrupt:16

```

---

### Post by Inspector Hector on 2005-11-06
Ok, i think i surrender the problem, but i need help for that.

It seems that my system is trying to route data through eth2 instead of eth0.
eth2 is my wireless card and should not be loaded by default. 
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:00:F0:95:16:2A
          inet Adresse:192.168.1.101  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::200:f0ff:fe95:162a/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95494 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:49677367 (47.3 MiB)  TX bytes:15377209 (14.6 MiB)
          Interrupt:16

eth2      Protokoll:Ethernet  Hardware Adresse 00:12:F0:2B:3F:81
          inet6 Adresse: fe80::212:f0ff:fe2b:3f81/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12807 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Basisadresse:0xe000 Speicher:c8010000-c8010fff

```

You can see how many Packages where send over eth2, and where received (this is also weird).

The Problem is still there when i'am disabling eth2. 

This must be set somewhere in my system, and i really don't know where. 
Could someone help?

---

### Post by mlomker on 2005-11-06
> This is a well-known bug...and it's drawn me closer to my friend Mr. Command Line. :P

**kdesu kcontrol** or **kdesu systemsettings** will work around most of it.  There are a couple sections (like File Sharing) that won't work even with that.

---

### Post by mlomker on 2005-11-06
> This must be set somewhere in my system, and i really don't know where. 
Could someone help?

I don't see anything wrong with your network setup, so I don't know.  Have you looked through the logs for errors?  They are all in /var/log.  kernel.log, messages, syslog, daemon.log

---

### Post by Inspector Hector on 2005-11-06
dmesg
```

[4299970.832000] eth2: no IPv6 routers present

```
daemon.log
```

Nov  6 14:52:57 localhost dhclient: No DHCPOFFERS received.
Nov  6 14:52:57 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 14:53:01 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 19
Nov  6 14:53:20 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
Nov  6 14:53:22 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
Nov  6 14:53:25 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
Nov  6 14:53:28 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
Nov  6 14:53:30 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
Nov  6 14:53:34 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
Nov  6 14:53:44 localhost dhclient: No DHCPOFFERS received.
Nov  6 14:53:44 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 14:53:47 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 17
Nov  6 14:54:04 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
Nov  6 14:54:14 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 9
Nov  6 14:54:23 localhost dhclient: No DHCPOFFERS received.
Nov  6 14:54:23 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 14:54:40 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov  6 14:54:43 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  6 14:54:48 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  6 14:54:53 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Nov  6 14:55:01 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Nov  6 14:55:15 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Nov  6 14:55:23 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Nov  6 14:55:37 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov  6 14:55:41 localhost dhclient: No DHCPOFFERS received.
Nov  6 14:55:41 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 14:57:48 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
Nov  6 14:57:52 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
Nov  6 14:57:56 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
Nov  6 14:58:07 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 9
Nov  6 14:58:15 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
Nov  6 14:58:24 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
Nov  6 14:58:26 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 20
Nov  6 14:58:30 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10
Nov  6 14:58:40 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 13
Nov  6 14:58:46 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
Nov  6 14:58:49 localhost dhclient: No DHCPOFFERS received.
Nov  6 14:58:49 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 14:58:53 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
Nov  6 14:59:02 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 20
Nov  6 14:59:22 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 3
Nov  6 14:59:25 localhost dhclient: No DHCPOFFERS received.
Nov  6 14:59:25 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 15:00:04 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
Nov  6 15:00:11 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 18
Nov  6 15:00:29 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 20
Nov  6 15:00:49 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
Nov  6 15:01:03 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 2
Nov  6 15:01:05 localhost dhclient: No DHCPOFFERS received.
Nov  6 15:01:05 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 15:02:13 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  6 15:02:18 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  6 15:02:23 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  6 15:02:29 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov  6 15:02:41 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17

```
syslog
```

Nov  6 15:02:13 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  6 15:02:18 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  6 15:02:23 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  6 15:02:29 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov  6 15:02:41 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Nov  6 15:02:58 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Nov  6 15:03:05 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Nov  6 15:03:14 localhost dhclient: No DHCPOFFERS received.
Nov  6 15:03:14 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 15:04:20 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
Nov  6 15:04:24 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
Nov  6 15:04:31 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Nov  6 15:04:32 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
Nov  6 15:04:36 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
Nov  6 15:04:39 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 20
Nov  6 15:04:41 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
Nov  6 15:04:49 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
Nov  6 15:04:59 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 13
Nov  6 15:05:00 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
Nov  6 15:05:07 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
Nov  6 15:05:12 localhost dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
Nov  6 15:05:17 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
Nov  6 15:05:21 localhost dhclient: No DHCPOFFERS received.
Nov  6 15:05:21 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 15:05:30 localhost dhclient: DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
Nov  6 15:05:33 localhost dhclient: No DHCPOFFERS received.
Nov  6 15:05:33 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 15:06:24 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
Nov  6 15:06:30 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 13
Nov  6 15:06:43 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 15
Nov  6 15:06:46 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Nov  6 15:06:54 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Nov  6 15:06:58 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 19
Nov  6 15:07:02 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Nov  6 15:07:13 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Nov  6 15:07:17 localhost dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
Nov  6 15:07:25 localhost dhclient: No DHCPOFFERS received.
Nov  6 15:07:25 localhost dhclient: No working leases in persistent database - sleeping.
Nov  6 15:07:32 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15

```

Uhm, does that mean my router is not working properly? I just checked in to check the settings, and everything seems nice. Also Windows is working with it without problems.

---

### Post by mlomker on 2005-11-06
> Uhm, does that mean my router is not working properly? I just checked in to check the settings, and everything seems nice. Also Windows is working with it without problems.

It looks like it's trying to get an address for your wireless card since it is in an **up** state.  None of those lines mention eth0, so I don't see a problem with what you posted.

---

### Post by Inspector Hector on 2005-11-06
I just disabled DHCP on my router, killed dhclient, and disabled eth2.
And the Problem is still there.

It looks like its trying to send trough eth2, and eth0 catches the response.

I searched for all eth0 in the logfiles

messages
```

Nov  6 13:05:55 localhost kernel: [4294674.612000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCIX:100MHz:32-bit) 10/100/1000BaseT Ethernet 00:00:f0:95:16:2a
Nov  6 13:05:55 localhost kernel: [4294674.612000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
Nov  6 13:05:55 localhost kernel: [4294674.612000] eth0: dma_rwctrl[76180000]
Nov  6 13:05:55 localhost kernel: [4294709.232000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Nov  6 13:05:55 localhost kernel: [4294709.232000] tg3: eth0: Flow control is on for TX and on for RX.

```
syslog
```

Nov  6 15:22:33 localhost dhclient: Listening on LPF/eth0/00:00:f0:95:16:2a
Nov  6 15:22:33 localhost dhclient: Sending on   LPF/eth0/00:00:f0:95:16:2a
Nov  6 15:22:35 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67

```
daemon.log
```

Nov  6 13:08:12 localhost dhclient: Listening on LPF/eth0/00:00:f0:95:16:2a
Nov  6 13:08:12 localhost dhclient: Sending on   LPF/eth0/00:00:f0:95:16:2a
Nov  6 13:08:13 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  6 15:22:33 localhost dhclient: Listening on LPF/eth0/00:00:f0:95:16:2a
Nov  6 15:22:33 localhost dhclient: Sending on   LPF/eth0/00:00:f0:95:16:2a
Nov  6 15:22:35 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67

```

And your're absolutely right, there isn't anything interesting about eth0.

---

### Post by Inspector Hector on 2005-11-06
Okay, now i'am totally confused.
I just installed Opera, which i like more the konqeror or firefox, and now surfing is as easy and fast as it should be. Till NOW! 
I'am just downloading some movies from the below zero conference at full rate.
I'am really lost for words.

---

### Post by mlomker on 2005-11-06
> I'am really lost for words.

I've seen those problems for people that didn't disable the IPV6 setting in Firefox, but one of your previous posts indicated that you had.

---

### Post by Inspector Hector on 2005-11-06
Disabled IPV6? Not, that i'am aware of.

Ok, i search trough the forum and found /etc/modprobe.d/aliases -> alias net-pf-10 ipv6
I commented it out. 

Guess i have to reboot, since i can't remove the module it's "in use".

But i'am still wondering how this could effect Konqueror, and Opera is untroubled.

---

### Post by mlomker on 2005-11-06
I was referring to [this setting]("http://www.ubuntuforums.org/showpost.php?p=32275&postcount=4") but perhaps that's a more global way of dealing with it.

---

### Post by Inspector Hector on 2005-11-06
I still don't know why Opera was not affected, but with disabled ipv6 it seems to work now, even for konqueror. 
Altough, dhclient is still needed to get the correct route (Of course, i enabled dhcp on my router for that).
So the huge amount of sent packages on eth0, must have come through its searching for a dhcp-connection. My router only accepts wpa, so there was no responding.

mlomker, thank you very much. I learned a lot, and i can have fun with Kubuntu again :)

---

### Post by jobi21 on 2005-11-06
Hm ... It seems that Kubuntu is having trouble with my Zyxel router (Zyxel ZyAIR B-200).

I tried connecting Kubuntu directly to my ADSL Router, which also has DHCP, and it worked for eth0 (e1000). Any ideas on how to troubleshoot this? When I use the Zyxel via eth0 I am unable to connect. When I try to use the Zyxel via eth1 (ipw2100/wireless) I am unable to connect. Additionally, when I run dhclient on eth1 my Zyxel router stops working! Here's my /etc/network/interfaces:

```
jobi@buddy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5). 
# The loopback network interface auto lo iface lo inet loopback address 127.0.0.1 netmask 255.0.0.0 
# This is a list of hotpluggable network interfaces. 
# They will be activated automatically by the hotplug subsystem. mapping hotplug script grep map eth0 
# The primary network interface 

auto eth0 
iface eth0 inet dhcp 

#auto eth1 
#iface eth1 inet dhcp 
#wireless-essid jobi 
``` 

I'm at loss here... The hardware in question has worked flawlessly when running other Linux distros: 

*Intel Corp. 82540EP Gigabit Ethernet Controller (using e1000) 
*Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (using ipw2100)
*Zyxel ZyAIR B-200

---

### Post by Inspector Hector on 2005-11-06
Did you try disabling ipv6 as i did?

---

### Post by jobi21 on 2005-11-06
[QUOTE=Inspector Hector]Did you try disabling ipv6 as i did?[/QUOTE]

Yes I did.

---

### Post by jobi21 on 2005-11-08
[QUOTE=jobi21]Hm ... It seems that Kubuntu is having trouble with my Zyxel router (Zyxel ZyAIR B-200).

I tried connecting Kubuntu directly to my ADSL Router, which also has DHCP, and it worked for eth0 (e1000). Any ideas on how to troubleshoot this? When I use the Zyxel via eth0 I am unable to connect. When I try to use the Zyxel via eth1 (ipw2100/wireless) I am unable to connect. Additionally, when I run dhclient on eth1 my Zyxel router stops working! Here's my /etc/network/interfaces:

```
jobi@buddy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5). 
# The loopback network interface auto lo iface lo inet loopback address 127.0.0.1 netmask 255.0.0.0 
# This is a list of hotpluggable network interfaces. 
# They will be activated automatically by the hotplug subsystem. mapping hotplug script grep map eth0 
# The primary network interface 

auto eth0 
iface eth0 inet dhcp 

#auto eth1 
#iface eth1 inet dhcp 
#wireless-essid jobi 
``` 

I'm at loss here... The hardware in question has worked flawlessly when running other Linux distros: 

*Intel Corp. 82540EP Gigabit Ethernet Controller (using e1000) 
*Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (using ipw2100)
*Zyxel ZyAIR B-200[/QUOTE]

Bump...

Does anyone know how I could troubleshoot this? Are there alternative dhcp-clients available for kubuntu that might work better?

---

### Post by mlomker on 2005-11-08
[QUOTE=jobi21]Does anyone know how I could troubleshoot this? Are there alternative dhcp-clients available for kubuntu that might work better?[/QUOTE]

No, but if the machine works when connected to your ADSL modem then it sounds more like a problem with your router than Ubuntu.  Does the Zyxel work from Windows or another operating system in general?

What is it giving you?

```

ifconfig eth0
sudo dhclient eth0

```

If you get an address:

```

route -n
cat /etc/resolv.conf
ping your.router.ip
ping 128.101.101.101
ping [www.mpr.org](www.mpr.org)

```

---

### Post by jobi21 on 2005-11-08
Well ... VICTORY! (I think)...

I de-installed dhclient and dhcp3 and installed dhcpcd (which always has been my weapon of choice) from universe (had to uncomment some lines in sources.list) and now both the wired and wireless works perfectly with the Zyxel.

Strange, but it works.

---

### Post by jccollin on 2006-12-20
I have been having the same issue with a Dell Latitude D505 with Broadcom 46xx serie. I was not able to get a DHCP lease at all. What I had to do was to comment the ipv6 line in /etc/modprobe.d/aliases and reboot my PC.
Everything works fine now !

---

### Post by jonkanon on 2006-12-23
"I have been having the same issue with a Dell Latitude D505 with Broadcom 46xx serie. I was not able to get a DHCP lease at all. What I had to do was to comment the ipv6 line in /etc/modprobe.d/aliases and reboot my PC.
Everything works fine now !"

-can someone tell me what comment to add? I have the same problem.

---

