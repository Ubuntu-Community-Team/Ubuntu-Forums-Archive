---
title: "nfs problems with toshiba a70 wireless"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by holiday on 2005-10-01
I can mount nfs using eth0 but over with the wireless on this Toshiba a70, I get a timeout from the server. tcpdump shows what looks to be an error. Anyone know of wireless issues with this laptop. I see references to sound problems, but i don't see anything about the wireless

The tcpdump problem is 'oui unknown'

Here's a snip.

sroom (192.168.0.100) is the server,
192.168.0.101 is the toshiba client.

21:01:56.557584 IP 192.168.0.101.952480849 > sroom.localdomain.nfs: 168 readdirp lus [|nfs]
21:01:56.562011 IP sroom.localdomain.nfs > 192.168.0.101.952480849: reply ok 147 2 readdirplus
21:01:56.563869 IP sroom.localdomain > 192.168.0.101: udp
21:01:56.636310 arp who-has 192.168.0.101 tell sroom.localdomain
21:01:56.636342 arp reply 192.168.0.101 is-at 00:11:f5:16:02:fc (oui Unknown)

---

