---
title: "Poor network after 9.10 upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by darkdesire on 2009-11-03
This seems to be a common issue but I cant find the solution. The network connections work but its really slow. I havea dual boot and MS Vista works fine. 
 
When connecting to a URL etc the initial connection is very slow after that it is not so bad.
 
/etc/resolv.conf shows my router as the nameserver.
 
ANy ideas wouldbe appreciated

---

### Post by pbrane on 2009-11-03
I have a router at work that does the same thing. It seems to be a problem with these routers. What I do at work is edit the /etc/resolv.conf file. If you know the actual DNS server addresses you can simply delete what Network-Manager has put in /etc/resolv.conf and replace with the nameserver address(es)

This is a pain but it will make your lookups MUCH faster. There is a thread on this that has other ways around the issue but I can't seem to find it right now.

---

