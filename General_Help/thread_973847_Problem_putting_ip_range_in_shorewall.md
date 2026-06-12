---
title: "Problem putting ip range in shorewall"
date: 2008-11-07
forum: General Help
---

### Post by sonicb00m on 2008-11-07
Does anyone know why the following command doesn't work any longer in shorewall rules?


ACCEPT net:85.225.1.1-85.225.254.254 fw tcp 4138


Setting up Rules...
iptables: No chain/target/match by that name
   ERROR: Command "/sbin/iptables -A net2fw -p tcp -m iprange --src-range 85.225.1.1-85.225.254.254 --dport 4138 -j ACCEPT" Failed

---

