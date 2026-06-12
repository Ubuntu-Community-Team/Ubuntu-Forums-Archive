---
title: "Upgrade killed my ethernet."
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by squashpup on 2009-06-09
Upgraded from 8.10 to 9.04 last night. Everything seemed to go well, no error messages, etc.  Now, however, when I start a browser...ANY browser, it works OK for about 30 seconds or so, then after that it refuses to load any pages.  

It has to be a problem with networking, I would think, as all browsers (Firefox, Epiphany, Galeon, Dillo) experience the same problem. 

What gives?  Do I now have the wrong driver for my ethernet?  Or, is there some setting I'm missing.

I have another computer running off the same router, albeit wirelessly. Everything works fine on it (using it now), so I'm not inclined to believe that it's a problem with my network.  

Any ideas are appreciated.

---

### Post by dstew on 2009-06-09
Post to the forum the output of```
ifconfig
```
If you can get pages initially, but then it stops, that sounds like a firewall configuration problem more than a basic connection problem. A basic connection problem usually results in no traffic at all. But, let's look at your ifconfig output anyway.

---

