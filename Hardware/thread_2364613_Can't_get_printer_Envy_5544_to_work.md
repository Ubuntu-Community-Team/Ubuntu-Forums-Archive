---
title: "Can't get printer Envy 5544 to work"
date: 2017-06-25
forum: Hardware
---

### Post by tomsax on 2017-06-25
Can anyone help me get it working.  I installed hplip some time ago and it worked sporadically but now it has failed completely.  I've tried to reinstall the latest hplip software but it doesn't work and I can't seem to remove the previous hplip software.

Tom

---

### Post by howefield on 2017-06-25
Moved to the "*Hardware*" forum for a better fit.

---

### Post by pdc on 2017-06-25
so tomsax you don't say which version of ubuntu you are using: as I understand it, hplip comes with each version of ubuntu; eg 3.16.3 comes with 16.04LTS ...... can you tell us what ```
dpkg -l hplip
``` gives please?

HP say your 5544 only needs 3.15.4 so we hear which version you are using as you say > I installed hplip some time ago

if you right-click on the icon for your HP in the PRINTERS folder; look under MAKE & MODEL and tell us what they says please ......... looking to see if it says hplip or maybe foomatic or somesuch ??

your device does **not** need a plug-in [http://hplipopensource.com/hplip-web/models/other/envy_5540_series.html](http://hplipopensource.com/hplip-web/models/other/envy_5540_series.html)

________
Hp have a site on hplip and they have a trouble-shooting page [http://hplipopensource.com/node/224](http://hplipopensource.com/node/224) and they suggest [http://hplipopensource.com/node/332](http://hplipopensource.com/node/332) you open a terminal and type ```
hp-check
``` and then run ```
hp-setup
```

.......... does that move things along a little?

---

