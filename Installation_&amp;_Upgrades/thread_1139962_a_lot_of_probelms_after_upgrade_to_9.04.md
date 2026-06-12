---
title: "a lot of probelms after upgrade to 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by James4 on 2009-04-27
hey,
I just upgraded from Interpid to Jaunty. during the upgrade process there some error which I don't remember but there was an alert saying after installation you must run /sbin/lilo manually.
now when I'm gonna run it it says 'Fatal: Cannot open: /etc/lilo.conf'.

there are some other, when I want to open synaptic it simply does not open. in terminal the 'Segmentation fault' occurs.
I can't open update manager either. the error is following:

```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.6/dist-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.6/dist-packages/cairo/_cairo.so: invalid ELF header
```
there is a sort of same problem with some other systematic apps.
help me please.

---

### Post by Djense on 2009-05-28
I am having similar problems.... a lot of things are just failing. Even running a command that should not run ( 'l' ), I get :
> 
$ l
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 8, in <module>
    import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/__init__.py", line 1, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 4, in <module>
    import sys, os, os.path, gdbm, posix, grp, string
ImportError: /usr/lib/python2.6/lib-dynload/gdbm.so: cannot read file data: Is a directoryI found [this]("http://www.ubuntu.com/getubuntu/releasenotes/904#python%20ImportError%20with%20systems%20upgraded%20before%20Ubuntu%209.04%20release%20candidate"), but it does not seem to help much...

Any idea somebody ?

---

### Post by Djense on 2009-06-08
Having exactly the same problem and still no luck with any solution...

---

