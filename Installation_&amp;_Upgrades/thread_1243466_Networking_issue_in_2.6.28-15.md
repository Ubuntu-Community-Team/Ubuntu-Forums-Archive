---
title: "Networking issue in 2.6.28-15"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by lordbah on 2009-08-18
Just let the system upgrade from 2.6.28-14 to 2.6.28-15 and now it can't find the wired network. The interface (eth2) is there and up, and according to ifconfig has an inet6 addr, but not the usual old-style IPv4 address - despite the fact that /etc/modprobe.d/blacklist.conf says "blacklist ipv6" so I don't think it should have an inet6 address at all. My router has not logged a DHCPREQUEST from the computer since the upgrade.

What can I check?

---

### Post by lordbah on 2009-08-18
I moved "blacklist ipv6" to a new file blacklist.local, and added a new file "aliases" containing "alias net-pf-10 off", and rebooted, and the issue is solved. Well, "ifconfig eth2" still shows an inet6 addr, but it also shows the old style "inet addr" that my network needs.

---

### Post by papadopc on 2009-08-18
Similar issue here, after upgrading to 2.6.28-15 the static ip configuration doesn't work

I don't see the inet6 address in ifconfig, and the solution above doesn't work for me

---

