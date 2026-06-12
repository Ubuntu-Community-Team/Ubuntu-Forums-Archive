---
title: "python being strange...."
date: 2008-11-15
forum: General Help
---

### Post by boblemur on 2008-11-15
Hey all im having problems with python reporting a "missing" module... however it is actualy there... 


first i run this and it fails:

```
nick@portable:~$ obmenu
Traceback (most recent call last):
  File "/usr/bin/obmenu", line 21, in <module>
    import obxml, gtk, gtk.glade, gobject, random, time, os, sys
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: No module named cairo
```

however from within python...
```
nick@portable:~$ python
Python 2.4.4 (#2, Apr 15 2008, 23:43:20) 
[GCC 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import cairo
>>> 
```

no problem at all :S any ideas... im running cli install + openbox

the only idea i had was... that it may be a python path problem but i really dont know

thanks for any help its much apreciated

---

