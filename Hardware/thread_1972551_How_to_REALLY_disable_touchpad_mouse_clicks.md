---
title: "How to REALLY disable touchpad mouse clicks"
date: 2012-05-03
forum: Hardware
---

### Post by yelimS on 2012-05-03
I've unchecked 'Enable mouse clicks with touchpad,' but it doesn't help. I've tried with 'Disable touchpad while typing' both checked and unchecked, they don't help either. Tried googling, but no luck. What do I do? Ubuntu 11.10

---

### Post by Xgen on 2012-05-03
[http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html]("http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html")

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

---

### Post by yelimS on 2012-05-04
Thanks, but that only lets me disable the touchpad entirely. I need the touchpad, just not the tap-to-click.

---

