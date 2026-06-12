---
title: "Have I got a problem here?"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by AJB2K3 on 2007-12-29
While looking through syslog for the cause of my network issue (yes ipv6 is globaly disabled along with nm_applet) I came accross this.

```

Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: reading /etc/resolv.conf
Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: using nameserver 192.168.1.1#53
Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: using nameserver 194.74.65.69#53
Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: using nameserver 194.72.0.114#53
Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: using nameserver 208.67.220.220#53
Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: using nameserver 208.67.222.222#53
Dec 29 08:47:50 ajb2k3-braincase dnsmasq[5051]: ignoring nameserver 127.0.0.1 - local interface
Dec 29 08:47:53 ajb2k3-braincase dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Dec 29 08:47:53 ajb2k3-braincase dhclient: DHCPOFFER from 192.168.1.1
Dec 29 08:47:53 ajb2k3-braincase dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Dec 29 08:47:53 ajb2k3-braincase dhclient: DHCPACK from 192.168.1.1
Dec 29 08:47:53 ajb2k3-braincase dhclient: bound to 192.168.1.150 -- renewal in 32834 seconds.
Dec 29 08:47:53 ajb2k3-braincase avahi-daemon[5367]: Withdrawing address record for 192.168.1.149 on eth1.
Dec 29 08:47:53 ajb2k3-braincase avahi-daemon[5367]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.149.
Dec 29 08:47:53 ajb2k3-braincase avahi-daemon[5367]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec 29 08:47:53 ajb2k3-braincase avahi-daemon[5367]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.150.
Dec 29 08:47:53 ajb2k3-braincase avahi-daemon[5367]: New relevant interface eth1.IPv4 for mDNS.
Dec 29 08:47:53 ajb2k3-braincase avahi-daemon[5367]: Registering new address record for 192.168.1.150 on eth1.IPv4.

```

```

Dec 29 09:12:34 ajb2k3-braincase kernel: [ 1541.548000] ata2.00: qc timeout (cmd 0xa0)
Dec 29 09:12:34 ajb2k3-braincase kernel: [ 1541.548000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Dec 29 09:12:34 ajb2k3-braincase kernel: [ 1541.548000] ata2.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
Dec 29 09:12:34 ajb2k3-braincase kernel: [ 1541.548000]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
Dec 29 09:12:39 ajb2k3-braincase kernel: [ 1546.588000] ata2: port is slow to respond, please be patient (Status 0xd1)
Dec 29 09:12:44 ajb2k3-braincase kernel: [ 1551.572000] ata2: device not ready (errno=-16), forcing hardreset
Dec 29 09:12:44 ajb2k3-braincase kernel: [ 1551.572000] ata2: soft resetting port
Dec 29 09:12:45 ajb2k3-braincase kernel: [ 1552.104000] ata2.00: configured for UDMA/33
Dec 29 09:12:45 ajb2k3-braincase kernel: [ 1552.104000] ata2: EH complete

```

BTW how do I get the 194 address to stay out of the files.
Have I got a problem here?

---

### Post by chewearn on 2007-12-29
194.74.65.69    UK    UNITED KINGDOM    PRIVATE CIRCUIT CUSTOMER NETWORKS     
194.72.0.114    UK    UNITED KINGDOM    SMDS CORE NETWORK

Does this looks familiar?

---

### Post by AJB2K3 on 2007-12-29
According to traceroute that was were I was lagging out.
Everytime I try to remove them they come back.

Can I set the file to read only to prevent it returning.

---

### Post by chewearn on 2007-12-29
> **AJB2K3 said:**
> According to traceroute that was were I was lagging out.
Everytime I try to remove them they come back.

Are they your ISP DNS?  It's probably propagated from your router because you use DHCP.  Couple of ways to fix this are discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=128254](http://ubuntuforums.org/showthread.php?t=128254)

> Can I set the file to read only to prevent it returning.
No, I don't think this will work.

---

