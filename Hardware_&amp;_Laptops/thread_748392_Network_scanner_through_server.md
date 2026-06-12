---
title: "Network scanner through server"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by franco.negri on 2008-04-07
Hi,
I am using a printer server to share my USB Officejet over my home network.

HPLIP does not work through this kind of servers (painfully discovered after many tries), anyway I managed to print with no problem, but not scanning, as the SANE port (6556) is not to be seen on the server:

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-04-07 19:14 CEST
Interesting ports on 192.168.1.100:
Not shown: 1712 closed ports
PORT     STATE SERVICE
80/tcp   open  http
9100/tcp open  jetdirect

While scanning through the same port gives no problem on the same machine running Windows.
Could you pleeeaaase help me?

---

### Post by pseudo-random on 2008-04-07
Perhaps its open but its a UDP port. Try a UDP scan instead of TCP.

---

### Post by franco.negri on 2008-04-07
Thank you, even if
 /etc/services
sane-port	6566/tcp	sane saned	# SANE network scanner daemon

anyway,

Interesting ports on 192.168.1.100:
Not shown: 1485 closed ports
PORT     STATE         SERVICE
161/udp  open|filtered snmp
1900/udp open|filtered UPnP
5353/udp open|filtered zeroconf

still not getting forward, still, on Win is a breeze

---

