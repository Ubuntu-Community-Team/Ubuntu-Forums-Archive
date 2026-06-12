---
title: "can't connect using domain name"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by basbytes on 2005-09-17
I'm using a shared internet connection via a broadband router (ip: 192.168.1.1).
I can connect to websites using the IP address bun not when using the domain name.

I can ping the router and other computers on my network, also I can look into the shared folders on the other networked computers, no problem there.

My network settings:
IP address: 192.168.1.222 (ubuntu installed PC)
Subnet: 255.255.255.0
Gateway: 192.168.1.1
DNS: 192.168.1.1

I tried without a DNS address and using DHCP but that din't make a difference either.
When I use the Live CD on other (windows) PC's on my network then I have exactly the same problem then on the PC with has Ubuntu installed.

I't driving me bonkers!
Please help.

---

### Post by Abhi Kalyan on 2006-11-13
> **basbytes said:**
> I'm using a shared internet connection via a broadband router (ip: 192.168.1.1).
I can connect to websites using the IP address bun not when using the domain name.

I can ping the router and other computers on my network, also I can look into the shared folders on the other networked computers, no problem there.

My network settings:
IP address: 192.168.1.222 (ubuntu installed PC)
Subnet: 255.255.255.0
Gateway: 192.168.1.1
DNS: 192.168.1.1

I tried without a DNS address and using DHCP but that din't make a difference either.
When I use the Live CD on other (windows) PC's on my network then I have exactly the same problem then on the PC with has Ubuntu installed.

I't driving me bonkers!
Please help.
you might need to run a DNS and a DHCPO server. WHat happens is DHCP provides the IP's and the DNS connects the names to the distibuted IPs'.
Please set your NIC's to get IP via the DHCP. If this is not possible please edit.
1. /etc/nsswitch.conf
2. /etc/resolv.conf
3. /etc/hosts
Please be warned these files are important to the safe running of your system.
Please do check up on in other places before you do something.
Am a newbie too so dont trust me, These are just markers which might help you.
Cheers all the best.

---

