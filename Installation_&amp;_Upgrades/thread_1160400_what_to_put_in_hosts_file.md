---
title: "what to put in hosts file"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by alidayi on 2009-05-15
hello 
 
ui know this is goingto sound very stupid but ive been trying to setup a server using this thread [http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3-p3)
 
basically i have managed to do this but ipconfig ends up having a few hicups
so ive installed then reinstalled a few times.
 
basically i was wondering at step seven i use " nano /etc/hosts to go into the file at the top of the file i have been putting:
 
```
 
127.0.0.1           localhost.localdomain       hunserver1 (this is th ename of my server)
192.168.x.x       hunserver.kicks-***.net    hunserver1

```
 
hunserver.kicks-***.net is my DNS with Dyndns.
am is this right or im a supposed to put my hunserver1.hundomain.com which is my local domain which is set by me belkin router?
 
i hope this makes sense

---

### Post by Brandon Williams on 2009-05-15
The section about /etc/hosts in that howto doesn't make a lot of sense to me. The server should typically identify itself to itself as a localhost. The standard ubuntu install will have done that already, adding a line like this:

    127.0.1.1	myhostname.mydomain myhostname

This is because you would ordinarily want to use the localhost address to connect to yourself, not the external address.

Here's what my config looks like. I have an ssh server that is publicly accessible via port-forwarding configured in my router. The router also provides local dns. My router's local dns is configured to provide the private, internal address if I request my dyndns hostname, so that I don't try to go outside my network in order to get to my local server from another machine. My ssh server itself has an entry in its /etc/hosts file like the one I described above so that it will not try to go off the box in order to get to itself, and also so that it will always be able to resolve its own name, even if networking fails.

---

