---
title: "another iptables question"
date: 2008-07-24
forum: General Help
---

### Post by lotrnew on 2008-07-24
i'm trying to get port forwarding working 
3 interfaces 

eth1 192.168.2.0/24 internal net 
ppp0 external net - pppoe inet over 
eth0 192.168.1.0/24 

i'm trying to forward 110 port on eth1 to 10.10.10.1:110 on ppp0 

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 110 -j DNAT --to-destination 10.10.10.1:110 

what should I do?

---

### Post by tyce on 2008-07-24
This is how I do it...

iptables -t nat -A PREROUTING -p tcp --dport 110 -i eth1 -j DNAT --to-destination 10.10.10.1:110

---

