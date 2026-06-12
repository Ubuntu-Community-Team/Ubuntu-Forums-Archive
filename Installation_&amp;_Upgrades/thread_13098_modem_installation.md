---
title: "modem installation"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by john rudder on 2005-01-28
I am new to linux and i would like some help in connecting to the internet, i am using a d-link dsl-300t adsl modem.
I use wanadoo broadband as my server and i do not know how to proceed to connect this.

---

### Post by m4ng0 on 2005-01-29
If you are using PPP over Ethernet, just turn on your modem and, in a terminal, type:
sudo pppoeconf
[Password]
Answer the questions...
Finally it asks you if you want to activate the connection.

Once configured, you can start the connection whenever you want with:
pon dsl-provider
and disconnect with
poff

---

