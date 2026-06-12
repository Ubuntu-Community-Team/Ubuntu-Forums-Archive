---
title: "python and gtk issues"
date: 2008-07-23
forum: General Help
---

### Post by spudgunman on 2008-07-23
so im real stuck I have upgraded GTK to 2.12 and pygtk to 2.12 (well I think i did) and upgraded python 2.5 but check this out.. how can I upgrade GTK in python to show 2.12? i have been working on this problem for seems like 40 hours now any help would be super 

>>> import gtk
/usr/local/lib/python2.5/site-packages/pycairo-1.4.12-py2.5-linux-i686.egg/cairo/_cairo.py:3: UserWarning: Module gtk was already imported from /usr/local/lib/python2.5/site-packages/gtk-2.0/gtk/__init__.pyc, but /usr/local/lib/python2.5/site-packages/pygtk-2.12.1-py2.5-linux-i686.egg is being added to sys.path
  import sys, pkg_resources, imp
>>> import pygtk
>>> gtk.gtk_version
(2, 10, 14)
>>> gtk.pygtk_version
(2, 12, 1)
>>>

---

### Post by boblemur on 2008-07-23
you may have an odd problem that happens on windows(not sure about ubuntu) but you should try find gtk.pyc (the compiled python script) it will not have been update(or at least this is my guess...)

if in doubt.. backup gtk.py then edit it so that its got a syntax error in it... and then when you import if you dont get the syntax error u know ur not importing the file you think you are :P stupid but this has happened to me before, hope this works

---

### Post by spudgunman on 2008-07-24
i dont have 
.. /site-packages/gtk.py
.. /site-packages/gtk.pyc
.. /site-packages/gtk.pyo 

should pygtk have compiled them?

i dont have them on disk at all that i can locate.

in the error it shows Module gtk was already imported from /usr/local/lib/python2.5/site-packages/gtk-2.0/gtk/__init__.pyc

but those files look compiled fresh.


UPDATE: when I config pygtk i get this


The following modules will be built:

atk
pango
pangocairo
gtk with 2.10 API
gtk.glade
gtk.unixprint

How to I make it 2.12 API that is my issue... 

I have built GTK 2.12 but the lib's dont seem to drop into place?

---

