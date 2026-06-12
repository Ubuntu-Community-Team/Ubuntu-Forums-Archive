---
title: "Turbo core not working"
date: 2014-07-23
forum: Hardware
---

### Post by vishwendra_singh on 2014-07-23
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][/TD]
[TD="class: postcell, bgcolor: transparent"]I got ubuntu 14.04 on hp pavalion g6 with an amd apu a6 llano which has a stock frequency of 1500mhz and is capable of boosting to 2400mhz.
But on my system it's turbo boost feature is not working.

[/TD]
[/TR]
[/TABLE]

[IMG]https://www.dropbox.com/s/w4af80i46bli8b7/Screenshot%20from%202014-07-23%2020%3A34%3A42.png[/IMG]

---

### Post by Yellow Pasque on 2014-07-23
It's probably working. cpufreq just does not report the turbo frequency. You can test it with:
```
sudo modprobe -v msr
sudo cpufreq-aperf
```

---

### Post by vishwendra_singh on 2014-07-23
thanks dude it's working ...

---

