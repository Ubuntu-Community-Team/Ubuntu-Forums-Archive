---
title: "Screen switch off with recent kernel on my netbook samsung"
date: 2010-02-08
forum: Hardware
---

### Post by Thibaud74 on 2010-02-08
Hi,

I've got a problem of wifi with my netbook samsung m140 (same architecture that the m120, m130, maybe nc10 ?) : the wifi have stopped to work after a suspend to ram, whenever I fell back on screen. I used a UNR distribution with karmic 9.10 and the default 2.6.31-17-generic kernel.

Si I installed a more recent kernel with ppa sources, 2.6.33-020633rc5 and 2.6.32. This resolved my wifi problem. However, I've now a new problem. Whenever I unplug the netbook and use the battery, after few minutes, the screen goes black.

In these case, I can use my computer, it works, but I can't see anything. When I shift to console mode with ALT-F1, the screen stays black, and when I return in graphic mode with ALT-F7, nothing more happens. The only way is to press ALT-F2 and blind type "gnome-display-properties" and press Return key after to plug a second screen for auto-detection.

Thanks for help,
Thibaud.

PS : better to post elsewhere ?

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
```

---

