---
title: "Enabling Desktop Effect"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by developer_anish on 2009-07-04
I've a problem.... I'm using Ubuntu 9.10 (AMD64 Architecture)... and I want to enable my Desktop Effect in laptop...
I've Lenovo T61 laptop and is the Business Laptop... My graphics card is of Nvidia and my version is Nvidia Quadro NVS 140...
I downloaded the package but it's not working... whenever i want to install this software.. my whole system crash... so I'm in trouble...

how can I successfully run the desktop effect in my Laptop... can any 1 suggest from the scratch...
It'll be gr8 help for me....
thankx in advance...

---

### Post by drs305 on 2009-07-04
There is a script you can run that will look at your system and detemine its suitablility for compiz. You can get the script here - it's called compiz-check:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

compiz is installed by default in jaunty and later. What exactly is it you are trying to install? Or do you just mean when you try to enable "Desktop effects"?  One thing you might try is to turn off Metacity's compositing before you try to enable Desktop effects:
```

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false

```

---

