---
title: "Unable to connect to network"
date: 2008-08-30
forum: General Help
---

### Post by Blzut3 on 2008-08-30
I've recently switched from a wireless to a wired network.  Since I've been using my computer as a wirelss bridge I've had firestarter and a dhcp server installed.  Once I retrieved wires I felt the need to uninstall these programs.  The problem is now I'm unable connect to any other computer.  If I try to ping the router it returns a message similar to:

ping: sendmsg: operation not permitted.

Is there a way to fix this or do I have to reinstall linux?

---

### Post by monkeyking on 2008-08-31
post your /etc/network/interfaces file

---

### Post by Blzut3 on 2008-08-31
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
```

I've tried flushing the iptables and doing so temporarily fixes the problem.  (When I reboot I have to flush them again.)

---

### Post by monkeyking on 2008-08-31
What if you ifdown, and then ifup your ethernet.
Does this work?

You might need to add your eth0 to your interface file before being able to ifdown/ifup

---

### Post by Blzut3 on 2008-08-31
I found a solution.  Apparently my /etc/network/if-up.d/iptables was wiped so I added the flush commands there, rebooted, and everything is working fine.

```
#!/bin/sh

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

Thanks for attempting to help though.

---

