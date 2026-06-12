---
title: "basKet, disable kontact plugin"
date: 2008-07-16
forum: General Help
---

### Post by jeremy on 2008-07-16
I have been using basket note pads, which I like very much. However the kontact plugin has been causing kontact to crash regularly.

After a bit of hunting around I found that by editing (as root)
/usr/share/services/kontact/basket.desktop and changing the line
X-KDE-KontactPluginHasSummary=true to read
X-KDE-KontactPluginHasSummary=false
basket works fine as a standalone app.

---

