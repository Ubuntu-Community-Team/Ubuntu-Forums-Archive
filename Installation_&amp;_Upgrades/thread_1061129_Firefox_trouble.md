---
title: "Firefox trouble"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by bobomk on 2009-02-05
my firefox is kind of screwed up
addon trouble, and I might have accidentally removed some folders while trying to mv them (stupid mistake)
I tried to uninstall and install firefox again, but the addons are still there, and when I try to remove them, they ask me to restart firefox, I restart it and again the same request

is there a way to remove everything and install firefox clean?

---

### Post by Dies on 2009-02-05
Open a terminal and do

```
 rm -rf ~/.mozilla 
```

or open Nautilus then hit ctrl+h and move it to the trash. Restart Firefox.

That will reset Firefox to the defaults for your account, unfortunately it will also reset other Mozilla software like Sunbird if you have it, but not Thunderbird.

---

### Post by bobomk on 2009-02-05
that didn't help
I still can't uninstall/use the addons

---

