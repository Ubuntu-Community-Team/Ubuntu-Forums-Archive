---
title: "shiretoko hijacked firefox"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2009-09-01
So I installed the daily update shiretoko from mozilla and it coexisted quite nicely with firefox3.0 for a few weeks. Today I wanted to test something in Firefox and I cannot get it to launch anymore. The the executable usr/lib/firefox-3.0.13 now starts shiretoko. This is confusing. How do I get firefox back. 

I tried apt-get install firefox but it says it's already installed!

---

### Post by gradinaruvasile on 2009-09-01
Remove the shiretoko ppa from your sources, uninstall (with --purge) firefox, install firefox.

---

