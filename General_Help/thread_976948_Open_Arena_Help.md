---
title: "Open Arena Help"
date: 2008-11-09
forum: General Help
---

### Post by ComputerHermit on 2008-11-09
hey I seem to be haveing a problem with iptables rules and open arena when I dont use a script everything is fine but this is not secure 
here is my rules if any help that would be great 


# Open Arena
iptables -A INPUT -p udp -m multiport \--dport 27950,27960,27961,27981,10000,10040,27977,27970,27980,666 -j ACCEPT
iptables -A OUTPUT -p udp -m multiport \--dport 27950,27960,27961,27981,10000,10040,27977,27970,27980,666 -j ACCEPT
iptables -A INPUT -p udp -m multiport \--dport 29602,29773,29775,62856,27980,27983,2410,27955,27965 -j ACCEPT
iptables -A OUTPUT -p udp -m multiport \--dport 29602,29773,29775,62856,27980,27983,2410,27955,27965 -j ACCEPT

---

