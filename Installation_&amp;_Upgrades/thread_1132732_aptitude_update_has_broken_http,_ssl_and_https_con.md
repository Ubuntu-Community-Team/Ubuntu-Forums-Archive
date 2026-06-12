---
title: "aptitude update has broken http, ssl and https connections still work"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by trstn on 2009-04-22
Hi everyone, another weird problem has got me stumped, any help would be awesome.

First off, ubuntu 8.10, standard server install using this guide: [http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)

Now the problem.... Today I noticed an upgrade was available, a number of php5 files were upgraded, all seemed safe enough so I performed a sudo aptitude safeupgrade and now cannot access my server via http.

Https and ssl connections are fine, I can access webmin for example, but nothing on the http side of things.

I've tried remote computers and also tried accessing [http://localhost](http://localhost) on the server itself and have had no joy. HELP!

---

### Post by slakkie on 2009-04-22
Is there anything running on port 80?

```

netstat -nap

```

Have you tried restarting the apache process?

Did the upgrade change your apache config?

---

