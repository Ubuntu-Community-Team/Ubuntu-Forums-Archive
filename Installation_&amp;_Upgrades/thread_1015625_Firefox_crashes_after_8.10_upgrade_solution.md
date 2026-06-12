---
title: "Firefox crashes after 8.10 upgrade solution"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by stderr on 2008-12-19
Thought I may as well post this in case anyone else is experiencing it too. 

Post upgrade from 8.04 to 8.10, Firefox would simply crash after a few seconds of opening. Konqueror would open and function, but for websites would either display a error (within the browser) citing a program termination (on my PC - I figured something related to HTTP or suchlike), or would successfully load the webpage, albeit slowly and perhaps lacking stylesheets etc.

To cut a semi-long story short, removing 'wins' from the hosts: line of my /etc/nsswitch.conf file (and restarting appropriate services) solved the issue. I may well have added it manually under 8.04 (can't remember), but everything still functioned perfectly then. 

I figure something must have changed since then. Whether it's a bug in libnss_wins (or whatever it's called) or just a logical consequence of placing it there in the first place, I'm not sure.

HTH

---

### Post by fiskeben on 2008-12-22
I upgraded to Firefox 3.0.5 last week and experienced this problem immediately. After several rounds of trying other solutions found around here, I tried this. Now, Firefox has run for a few hours without problems.

But I actually need wins support. It would be nice to get this sorted out. Does anybody know whether it's a bug in Firefox or the wins library (or a third place)?

---

### Post by cb34 on 2008-12-22
[http://ubuntuforums.org/showthread.php?t=1011649](http://ubuntuforums.org/showthread.php?t=1011649) :D :D

---

