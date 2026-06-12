---
title: "Separate DNS for LAN and Internet"
date: 2008-09-06
forum: General Help
---

### Post by descentspb on 2008-09-06
When i connect to the internet through PPP, it replaces my LAN's DNS with its own. I need this for the internet to work, however, when i try to reach the LAN's computers by their DNS names, it does not work. Is there a way to use both DNS servers? The 1st one only for LAN, the 2nd for the internet. Thanks in advance.

---

### Post by fwre01 on 2008-09-06
You can use your local DNS to do both. You need to setup your local DNS to forward any queries it doesnt know to your ISP's name servers. Then you just configure the one nameserver on your PC, and tell your ppp client not to overwrite your DNS.

---

### Post by descentspb on 2008-09-06
Thanks, but that could be a solution if I had any control over the LAN DNS server. But I don't.

---

### Post by fwre01 on 2008-09-07
...ahhh, that would be a problem.

Iv never heard of a way of splitting your DNS queries between two servers. 

This would be quite cumbersome, but you could use your local host file, but if you have lots of records on your local DNS server it may be very hardwork, just a thought. Then just point your /etc/resolv.conf to the ISP name server.


**EDIT**

Wouldn't listing both the name servers in /etc/resolv.conf work. Surely if it cant resolve a name from the first name server (i.e, the LOCAL DNS) it would then query the second.

---

