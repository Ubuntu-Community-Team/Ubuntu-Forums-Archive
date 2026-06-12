---
title: "Unable to ping LAN computer - 9.0.4 Server"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by eholz1 on 2009-07-02
hello all,

I have just installed Ubuntu Server, 9.0.4.  I can set the system
for DHCP, and my router will set the ip for the server.
I can ping the outside world (like 4.2.2.2, etc) and the router,
192.168.2.1 no problem.  I have other computers on the lan (windows xp and a MAC) with ip 192.168.2.103, and 192.168.2.104.
I can ping the Ubuntu server from either of these boxes, its ip is 192.168.2.100.  I cannot ping either of these lan boxes from the server.  I did not have this issue with Ubuntu server 8.0.4.

If I set the server for static ip, I have the same symtoms.
I do not require a DNS, these boxes are just on a LAN, and I want to run Samba, etc.

What am I missing?  I have seen some posts in regard to the resolv.conf file, and made changes there, but to no avail.

Any suggestions?

thanks

eholz1

---

### Post by Boondoklife on 2009-07-02
Well my first thought would be a firewall on the LAN boxes seeing how they can talk to the server but the server can not talk to them. Try setting up a share on the windows pc and try to browse the share from the server, or install vnc on the windoes box and try to connect to it from the server.

---

### Post by eholz1 on 2009-07-02
Hello Makatek,

no firewall running on the widows box (or mac).  I also checked to insure that Norton Internet security was not blocking, but
I will double check that again!

Thanks,

eholz1

---

### Post by eholz1 on 2009-07-03
Hello Malatek, et all.

Yep.  Brainfade, recheck the norton program, it was "protecting"
my LAN.

Thanks

eholz1

---

