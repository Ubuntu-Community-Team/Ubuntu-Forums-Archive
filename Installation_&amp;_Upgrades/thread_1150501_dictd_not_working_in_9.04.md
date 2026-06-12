---
title: "dictd not working in 9.04"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by thet on 2009-05-06
hey all,

i have dictd and some dictionaries installed for offline use. but since 9.04 it isn't working anymore.

dictd is getting startet but a portscan does not report dictd listening anywhere.

it does not work even if i start dictd after killing remaining dictd processes like so:
```
sudo dictd -p2628 --listen-to localhost
```

is there a firewall activated?
but
```
sudo ufw status
```
reports
Status: inactive

any hints?

---

### Post by thet on 2009-05-20
resolved:

you have to use **127.0.0.1** instead of localhost for hostname in gnome-dict dictionary-source preferences.

:)

---

