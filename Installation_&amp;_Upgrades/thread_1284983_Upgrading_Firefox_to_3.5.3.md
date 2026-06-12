---
title: "Upgrading Firefox to 3.5.3"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by csrobins on 2009-10-07
Hey guys, I upgraded to Firefox 3.5 a while back, and I thought I had the latest 3.5.3, but I noticed that the "About Mozilla Firefox" window as well as "firefox --version" both return version 3.5.1

I'm confused because Synaptic reports my "firefox-3.5" package as version "3.5.3+build1+nobinonly-0ubuntu0.9.04.2" Anyone know what the deal is? Or any ideas how I can find out which version I'm actually using. And if I'm only using 3.5.1 how I can get 3.5.3?

For reference, I don't have any mozilla repos installed.

---

### Post by aysiu on 2009-10-07
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
ls -l /usr/bin/firefox
ls -l /opt
dpkg -s firefox-3.5
dpkg -s firefox-3.0
cat /etc/lsb-release
uname -a
```

---

