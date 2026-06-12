---
title: "Internal Courier modem"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Howard Kaikow on 2007-05-14
I've tried running from LiveCD, version 7.04.

I installed gnome-ppp, and it successfully identified my modem on ttys1.
I was able to dial out and my ISP confirmed that I was connected.

But, Firefox cannot find any URL.
Evolution can find neither the incoming nor outgoing mail servers.
I cannot ping anyone.
I cannot ftp.

My ISP cannot ping me.

I am using a an internal Courier dial up modem.
Could Linux be trying to go thru the router, not connected to the internet, that I use for my local network?
Is there a linux firewall issue?

Here's more info.

> --> PPP negotiation detected.
--> Starting pppd at Sun May 13 19:30:09 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 12012
--> Using interface ppp0
--> local IP address [I removed address here]
--> remote IP address [I removed address here]
--> primary DNS address [I removed address here]
I can ping the local and remote IP addresses, but not the DNS address.


Are the Warnings above relevant to my problem?

---

