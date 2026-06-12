---
title: "3com network problem"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by red_Marvin on 2006-03-25
I installed ubuntu-server on an old dell laptop and it works well, and recently I also 
got hold of the docking station, with a network card (3com 3c905 100Base TX [Boomerang])
so I thought of the possibilites and decided to reinstall ubuntu (I'm still stuck in the
windows manners: big change=total reinstall) so it would detect and install the NIC too.

That didn't work.
On installing it fails on "configuring the network with DHCP", no matter if it's plugged into the ADSL modem or not,
(On -this- computer that I write this on it didn't fail, and it's connected the samme way)

However, on the installation I already have on the laptop, it atleast detects the
nic, (shows up on lspci etc.) However lshw -C network says "*-network DISABLED"
Could anybody perhaps help me get this up and running?
I've searched the forum, but the only other thread about this is dated -04.

---

### Post by jamesr on 2006-03-25
Lets starts to see if the NIC is detected correctly

Post the outputs of
```
sudo ifconfig -a
dmesg |grep eth0
```

and yes, I realise that you say it is detected

---

### Post by red_Marvin on 2006-03-26
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:C0:4F:F6:B6:EB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xfc80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1264 (1.2 KiB)  TX bytes:1264 (1.2 KiB)
```

dmesg:
```
[4294699.847000] eth0: Dropping NETIF_F_SG since no checksum feature.
```

---

### Post by red_Marvin on 2006-03-26
I just noticed that there is a special network subforum, if someone with mod powers 
perhaps could move it (if deemed appropirate) and then I would delete this post...

---

### Post by jamesr on 2006-03-27
Try```
sudo dhclient eth0
```

and post the output

---

### Post by red_Marvin on 2006-03-28
```
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00/c0:4f:f6:b6:eb
sending on   LPF/eth0/00/c0:4f:f6:b6:eb
Sending on  Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
```

The interval numbers were different all times I run the program, but it made no difference
if I had the network cable in or out, at running time and/or booting time.

---

### Post by jamesr on 2006-04-04
Sorry about the delay but I seemed to miss your reply. Have you got the problem?.

---

### Post by red_Marvin on 2006-04-05
As I have little (or less) knowledge of networking, I'm afraid that the problem
still exists.

---

### Post by az on 2006-04-05
[QUOTE=red_Marvin]
On installing it fails on "configuring the network with DHCP", no matter if it's plugged into the ADSL modem or not,
.[/QUOTE]


Does your adsl modem have an integrated router?  Because it would typically just do pppoe.  To connect directly to a modem that does pppoe, run

sudo pppoeconf
and enter your isp username and password.

If your modem does do dhcp (because it is also a router) your ethernet card is broken.

---

### Post by red_Marvin on 2006-04-05
pppoeconf detects eth0, but times out on the "access concentrators"
And about the modem+router thing: I have no Idea. The modem is connected to 
the computer with a standard network cable.

---

### Post by jamesr on 2006-04-05
I have downloaded the manual so I believedd but as yet I have not read it but it seems to be for  a standard router ie separate from the Modem so perhaps I have the wrong manual.

---

