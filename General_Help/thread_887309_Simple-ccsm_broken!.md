---
title: "Simple-ccsm broken!"
date: 2008-08-12
forum: General Help
---

### Post by ripps818 on 2008-08-12
Whenever I try to use simple-ccsm, it crashes and I get this output:
```
ripps@ripps-desktop:~/bin$ simple-ccsm
Traceback (most recent call last):
  File "/usr/bin/simple-ccsm", line 949, in <module>
    mainWin = MainWin(context, page)
  File "/usr/bin/simple-ccsm", line 865, in __init__
    self.EdgePage      = EdgePage(self.Context, self.GladeXML)
  File "/usr/bin/simple-ccsm", line 826, in __init__
    self.EdgeSelector = ccm.GlobalEdgeSelector(self.Context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Widgets.py", line 802, in __init__
    EdgeSelector.__init__ (self)
  File "/usr/local/lib/python2.5/site-packages/ccm/Widgets.py", line 523, in __init__
    self._base_surface = cairo.ImageSurface.create_from_png (background)
cairo.Error: file not found

```

---

### Post by ripps818 on 2008-08-14
Bumping for lack of explanation.

---

