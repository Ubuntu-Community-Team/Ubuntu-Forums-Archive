---
title: "Infrael - python script to translate wiimote IR tracking into mouse events"
date: 2009-01-20
forum: Hardware
---

### Post by wizgrav on 2009-01-20
Hello, I recently wrote a python script for IWBs based on Lee's concept.
[[COLOR="SandyBrown"]Source, win32 exe, a deb and docs are here [/COLOR]]("http://code.google.com/p/infrael/downloads/list"). Please post your feedback.
I haven't really tested on MacOSX so if anyone dual boots I'd be grateful.

---

### Post by mrjohnston on 2009-05-13
With the latest deb on jaunty it pulls an error

Traceback (most recent call last):
  File "/usr/bin/infrael", line 985, in OnExit
    diag=wx.FileDialog(None,"Select gesture command or cancel for precision
clicking",gstpath,gstfile,style=wx.FD_OPEN)
AttributeError: 'module' object has no attribute 'FD_OPEN'

Posted the defect on the site, and can't seem to connect the wiimote so I assume I or the program is doing something wrong.

---

