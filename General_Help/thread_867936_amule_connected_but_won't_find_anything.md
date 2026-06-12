---
title: "amule connected but won't find anything"
date: 2008-07-23
forum: General Help
---

### Post by pilotopirx on 2008-07-23
I am running xubuntu+kde (this allowed me to have a very lean system, but still get kde). Amule used to work, that is: connect, find files, download them. Now it connects just fine, but any search (I mean, even "britney"),  local or global will return no results. 

The preferences say TCP port 4712 UDP port 4714.
Bandwith limits download 80kB/s Upload 29kB/s. 

I opened those with 

sudo iptables -A INPUT -p udp --dport 4714 -j ACCEPT

(I can use the command line)

---

