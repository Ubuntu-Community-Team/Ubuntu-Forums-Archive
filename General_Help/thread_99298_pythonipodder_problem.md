---
title: "python/ipodder problem"
date: 2005-12-05
forum: General Help
---

### Post by tommmm on 2005-12-05
When I run ipodder or Castpodder I get some strange errors. ipodder used to work, but now doesn't. Here is the traceback, can anyone help?

Traceback (most recent call last):
File "/usr/share/ipodder/iPodderGui.py", line 21, in ?
import wx
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
from wx._core import *
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13405, in ?
from _misc import *
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc.py", line 4, in ?
import _misc_
ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc_.so: symbol wxDefaultVideoMode, version WXU_2.6 not defined in file libwx_gtk2u_core-2.6.so.0 with link time reference
thomas@ubuntu:~$

I may have added some python libraries at some point before it broke, should I try and remove everything python related and reinstall?
Thanks!

---

### Post by rowck001 on 2006-04-28
Wont get any help here mate!

noone knows anything (or they are too arrogant to share)

goto redhat FC4 and you will have no problems!!

---

