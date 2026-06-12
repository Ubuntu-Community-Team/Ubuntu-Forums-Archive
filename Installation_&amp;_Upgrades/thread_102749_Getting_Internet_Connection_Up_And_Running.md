---
title: "Getting Internet Connection Up And Running"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by Maupertus on 2005-12-12
Now, this may seem strange, but I've never had any problems running Ubuntu, but now I just can't seem to get connected to the internet.

In windows, everything is working just fine. I tried copy-ing settings from windows to Ubuntu, but came to the conclusion that my provider wants me to "automaticly get IP-adress".

How can I get it to work in Ubuntu?

---

### Post by az on 2005-12-12
"automaticly get IP-adress".

DHCP does that.  Statip IP address is the default in the network tool, but DHCP is what you want.  (We are talking about a network card. eh?)

You may also have pppoe

sudo pppoeconf.

---

