---
title: "Uninstalling AWN"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by William24 on 2009-04-23
Hi,

I searched this forum for "How to uninstall AWN". I got a few results and used one of them, but when I run the commands this is what I get:

[IMG]http://i476.photobucket.com/albums/rr122/SilvaMo0n/Help.jpg[/IMG]
Any help?

---

### Post by Tim Sharitt on 2009-04-23
Unless you are not using awn-bzr from a ppa, you just need

```
sudo apt-get remove --purge avant-window-navigator avant-window-navigator-data libawn0
```

without the -bzr on the end.

---

