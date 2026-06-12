---
title: "Missing Python package?"
date: 2008-09-02
forum: General Help
---

### Post by ezekiel000 on 2008-09-02
Can anyone help me? I've been trying to get Tundra ([http://rebui.ld.net.au/software/tundra](http://rebui.ld.net.au/software/tundra)) to run but when I start it in the terminal I get the following:

ezekiel@alice:~/Games/Tundra/src$ python tundra.py
Traceback (most recent call last):
  File "tundra.py", line 2, in <module>
    import globals as g
  File "/home/ezekiel/Games/Tundra/src/globals.py", line 12, in <module>
    import cache
  File "/home/ezekiel/Games/Tundra/src/cache.py", line 17, in <module>
    import style
  File "/home/ezekiel/Games/Tundra/src/style.py", line 14, in <module>
    import xml.sax.writer
ImportError: No module named writer

What am I missing I have: python-imaging, python-pygame & python-xml2 installed I thought that this was all that was needed from looking at the site.

---

### Post by unutbu on 2008-09-02
It's in PyXML:

[http://mail.python.org/pipermail/python-list/2006-August/400585.html](http://mail.python.org/pipermail/python-list/2006-August/400585.html)
[http://pyxml.sourceforge.net/](http://pyxml.sourceforge.net/)

It doesn't appear to be in the repos, however.

---

### Post by NoobixCube on 2008-10-09
I recently had exactly the same problem.  This probably seems obvious to more experienced users, but it took  me a while to figure out why PyXML wasn't installing correctly.  You have to make sure you have the Python dev packages installed too or the Build script won't work.  Once that's done, Tundra will work.  One problem though:  no sound.  There are music packs available on the Tundra site, but the developer hasn't implemented sound effects yet, so no "yippee!"s or "oh no!"s :P

---

