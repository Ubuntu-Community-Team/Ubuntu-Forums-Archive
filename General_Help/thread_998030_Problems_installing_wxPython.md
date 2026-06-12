---
title: "Problems installing wxPython"
date: 2008-11-30
forum: General Help
---

### Post by agentsmith270288 on 2008-11-30
I am trying to install wxPython so I can build GUI programs in Python. I updated Ubuntu Python to 2.6 and I assumed wxWidgets etc would be installed as well. When running my program I keep getting following error message:
```

Traceback (most recent call last):
  File "window.py", line 12, in <module>
    import wx
ImportError: No module named wx

```

I exhaustively checked every installation tutorial available and still I can't fix the issue. I have the following packages installed:
python-wxgtk2.6
python-wxgtk2.8
python-wxtools
libglibmm-2.4-dev
as well as a lot of others with similar names. I tried following the tutorials on wxPython website and it still doesn't work. Can some suggest a fix for this? Is there a straightforward way of installing wxPython through terminal or something? thanks

---

### Post by pirveli on 2009-02-25
I have pretty the same problem:
I have python2.5 only and I wanted to install wxPython. From Synaptic I chose python-wxgtk2.8 package and after installation I can't import wx because `No module named wx`.

How to solve this problem?

---

