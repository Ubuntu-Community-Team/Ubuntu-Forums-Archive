---
title: "problems configuring eth0 with DNS, gateway and subnetmask"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by tameritoke on 2005-12-26
Hi! 
I have a static IP-Address configuration from my ISP. The configuration runs successfully on Win and on Linux the configuration have to be done too.

The ISP gave me 1 IP, 2 DNS Addresses, 1 gateway, 1 subnetmask which I have to save at my kubuntu linux system.

If I run ifconfig, I discover ubuntu took the IP-Address, the Subnetmask but not the Gateway which is the Address of my DSL Router (10.0.0.138)

Also, the nameserver addresses. Where do they have to be listed?
Do the DNS-Server addresses need to be listed in the resolv.conf or in the interfaces file? 

If I activate the suboption 
nameserver xxx.xxx.xxx.xxx in the interfaces file while taking it away from the resolv.conf, I receive an errormessage. 

For any help solving my problem, I would thank


Tamer

---

### Post by Lambert on 2005-12-26
Make your interface file in this format

```
iface eth0 inet static
             address 192.168.0.111
             netmask 255.255.255.0
             gateway 192.168.0.1
             dns-search somedomain.org
             dns-nameservers 195.238.2.21 195.238.2.22
```

just replace all the correct data

---

### Post by tameritoke on 2005-12-27
It is still not working! I am going crazy!!! 
:mad: 

Here is the /etc/network/interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface


auto eth0

iface eth0 inet static
address 81.10.53.22
netmask 255.255.255.252
gateway 10.0.0.138
dns-search lan
dns-nameservers 163.121.128.134 212.103.160.18

and the /etc/hosts:

127.0.0.1 localhost.localdomain localhost ubuntu
# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

What did I make wrong?

---

### Post by Lambert on 2005-12-27
What's the output of this command

```
route
```

---

### Post by tameritoke on 2005-12-27
The command route: 

Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
81.10.53.20     *               255.255.255.252 U     0      0        0 eth0

and the command ifconfig: 

eth0      Protokoll:Ethernet  Hardware Adresse 00:0C:6E:FF:B0:2A  
          inet Adresse:81.10.53.22  Bcast:81.255.255.255  Maske:255.255.255.252
          inet6 Adresse: fe80::20c:6eff:feff:b02a/64 GÃ¼ltigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:788 (788.0 b)  TX bytes:378 (378.0 b)
          Interrupt:23 Basisadresse:0xa400 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:4738 (4.6 KiB)  TX bytes:4738 (4.6 KiB)

---

### Post by Lambert on 2005-12-27
try this

```
sudo route add default gw 10.0.0.13 dev eth0
``` 
if it works then add this line to your interfaces file

post-up route add default gw 10.0.0.13 dev eth0

---

### Post by tameritoke on 2005-12-27
sudo route add default gateway 10.0.0.13 eth0
SIOCADDRT: Das Netzwerk ist nicht erreichbar

sudo route add default gateway 10.0.0.138 eth0
SIOCADDRT: Das Netzwerk ist nicht erreichbar

Both are telling me that the network is not reachable :(

---

### Post by wanger123 on 2005-12-28
Hi there, I'm pretty sure you just need to remove this bit: 

address 127.0.0.1
netmask 255.0.0.0

and you should be good to go. I always have this problem when I mess with my wireless connection. I cant use my wired-ethernet until I remove these lines.

hope this helps
wanger

---

### Post by wanger123 on 2005-12-30
so how did you get on with this tameritoke?
wanger

---

