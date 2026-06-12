---
title: "Very strange routing problem"
date: 2008-09-26
forum: General Help
---

### Post by fragtion on 2008-09-26
Hey guys,
I've stumbled accross a bit of a strange issue with routing when using a linux server as the gateway for my network's windows machines.

What happens is that if I set the default gateway on my XP desktop machine to point to my windows server (which is sharing an internet connection with rras), routing works normally; but if I set the gateway IP to my linux server, then every internet IP I access gets added to the dynamic active routes on the windows box automatically, as if there was some kind of route pushing going on, and so I end up with a long list of IP's in my windows box's routing table, which is annoying because if I decide to change those routes on the linux box, it doesn't reflect recursively on the windows clients so they point to the wrong destination.

Here's an example of what I'm saying
Let's say 192.168.0.2 is the windows server with the internet connection, 192.168.0.1 is the linux server, and 192.168.0.3 is my desktop XP machine.
192.168.0.1 (linux box) has 'default via 192.168.0.2 dev eth1' (windows machine with internet)
I set my XP machine's default gateway to 192.168.0.1, so that it looks like this:  192.168.0.3->192.168.0.1->192.168.0.2->Internet
I establish a TCP connection to the internet, to an IP such as 196.35.1.1 on my XP machine through the linux gw.
I then end up with an active entry like this in my XP routing table, skipping 192.168.0.1 for 192.168.0.2:
[quote="ROUTE PRINT"]
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
        196.35.1.1        255.255.255.255        192.168.0.2       192.168.0.3       1
[/quote]
Now say I decide to make a pppoe connection on the linux box and no longer have 192.168.0.2 default route on the linux machine, the temporary route is still sitting on the XP machine and I have to pysically remove it.

I dont want it to dynamically add the routes, I just want a single static gateway. It works properly like this if I set the gateway as the windows server, but I'd prefer to have it done properly using linux -- ie: i'd like to know what's causing this strange problem.

Any insight would be appreciated =)

---

### Post by fragtion on 2008-10-07
.. Surprised no-one was familliar with this one, took me ages to find the solution, but seems I've found it. Setting the following seems to have solved the problem:
[quote=/etc/sysctl.conf]
net.ipv4.conf.default.send_redirects=0
net.ipv4.conf.eth1.send_redirects=0
net.ipv4.conf.all.send_redirects=0
[/quote]
Obviously you'd replace eth1 with whatever interface you're experiencing the problem with.

---

