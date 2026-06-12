---
title: "Printer Installation - Several Sub-nets"
date: 2017-03-01
forum: Hardware
---

### Post by shadragon on 2017-03-01
Morning, 

I have a 14.04 Kubuntu LAMP server I'm trying to get a printer hooked up too. 

The HP LaserJet P3015 Printer in question is on a dedicated sub-net for support devices like NAS, printers, etc. (192.168.17.0/24) 

The Printer is shared off of a Windows 2012 server that is on the Corp network (192.168.18.0/24). 2012 Server has multiple NIC's and is on both Corp/Guest networks and has access to the Printer 17.0 sub-net.

The LAMP server is a VM on our Guest network (192.168.0.0/23). By policy, it has no path to get to the 17.0 sub-net.

The LAMP server can ping the 2012 server on the Guest network, but I can't seem to connect to the printer share. I can connect Windows machines on Guest to that print share without issue. 

Any tips?

---

### Post by ajgreeny on 2017-03-01
Duplicate of [https://ubuntuforums.org/showthread.php?t=2354295&p=13614335#post13614335](https://ubuntuforums.org/showthread.php?t=2354295&p=13614335#post13614335)
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 

Closed

---

