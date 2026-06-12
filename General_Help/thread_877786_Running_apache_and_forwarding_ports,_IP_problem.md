---
title: "Running apache and forwarding ports, IP problem"
date: 2008-08-02
forum: General Help
---

### Post by Bonez56 on 2008-08-02
Hi all

A friend of mine set up a Ubuntu Hardy server last night and he has a D-Link 604T ADSL router.

We installed and set up apache2 as we wanted to run a web site.

Ports 80 and 443 have been forwarded via his router to the internal IP of the server (192.168.1.99), but whenever I try to access his WAN IP address from outside of his LAN, it connects, then immediately tries to forward me to 192.168.1.99 - this might sound silly but that is what shows up in my browser and I am not inside his network.

Obviously since i'm outside his network, and I don't have a server inside my LAN with that IP, it just fails to connect.

I am pretty sure it's not a problem with the router because I also set up a port forward for port 22 (SSH) the exact same way and I can connect to SSH fine.

It appears that apache2 is binding to the local IP address of the NIC in his server. I checked all the apache2 config files but could not find any trace. Any suggestions?

Thank you

---

### Post by ethernet on 2008-08-17
Same problem here. Using SSL, for all it matters, and get the same 404 when accessing the server using my dyndns account but no issues with remote SSH. Have enabled ufw and allowed tcp on 80 and 443 but no good.

---

### Post by cariboo on 2008-08-17
Go here:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

To make sure your ports are open and visible to the world.

Jim

---

### Post by ethernet on 2008-08-18
> **cariboo907 said:**
> Go here:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

To make sure your ports are open and visible to the world.

Jim
Thanks for the link. Found it on another thread as well. Surprisingly, port 80 and 443 are open so my router's firewall rules are working anyway.

---

