---
title: "DP-301P+ Printer Server Connection Problem"
date: 2009-06-24
forum: Hardware
---

### Post by mark bower on 2009-06-24
Task:  Connect to my HP LJ4 printer via a Dlink DP-301P+ print server, using CUPS.

System:
1)Ubuntu 9.04, IP address for print server(PS) given as 192.168.0.10 (in setup guide)
2)printer parallel port>DP-301P>CAT-5>Linksys router WRT54G port
3)computer>CAT-5>WRT54G port
4)complete system involves 2 additional computers to route via wireless to the PS and printer, these in addition to the primary computer in 3)  

Tried:
I used sudo dpkg-reconfigure cups and set the backend to “socket”.  I tried a number of combinations like:  http://localhost:631>add printer>name printer>Internet Printing Protocol (ipp)>device URI (eg socket://192.168.0.10)>make (HP)>model HPLJ4 Plus hpijs(en)>passwd stuff.  Eventually get the message “Attempting to connect to host < socket://<IP used> on port 9xxx”, but no connection.

Ifconfig -a, and lshw -C network do not seem to locate the DP-301P, and I suspect this might  have to do with the router DHCP changing the default PS IP to a different IP?

Help please.

---

### Post by mark bower on 2009-06-27
bump

---

### Post by mark bower on 2009-06-28
bump

---

