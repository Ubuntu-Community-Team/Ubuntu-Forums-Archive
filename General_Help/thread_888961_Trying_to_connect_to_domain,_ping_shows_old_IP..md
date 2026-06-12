---
title: "Trying to connect to domain, ping shows old IP."
date: 2008-08-13
forum: General Help
---

### Post by Dave_Connor on 2008-08-13
When I try to ssh to my domain a friend help setup, ssh says "no route to host" and when I ping the domain, it shows my old IP on the domain and yet it should have updated with my current IP. I restart apache2 but this didn't fix this issue. any help here ?

---

### Post by RealPSL on 2008-08-16
Restarting apache is not going to resolve that problem. It seems that you have a problem resolving your target hostname to the correct IP address. If you are the one managing the DNS system then you would need to make sure it was updated correctly. Until then you probably want to make sure that you can connect by using the correct IP address.

---

