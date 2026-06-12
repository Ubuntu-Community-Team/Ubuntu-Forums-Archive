---
title: "Python Graphics Module and _tkinter"
date: 2008-07-12
forum: General Help
---

### Post by bcerge on 2008-07-12
I am trying to write a program using the graphics.py module, there is nothing wrong with the module, but when I go to run the program, i get this:

 File "Avalanche.py", line 3, in <module>
    from graphics import *
  File "/usr/lib/python2.5/site-packages/graphics.py", line 93, in <module>
    import Tkinter
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 41, in <module>
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: No module named _tkinter, please install the python-tk package

I can't find the python-tk package anywhere.....
thnx in advance.

---

### Post by boblemur on 2008-07-13
```
sudo apt-get install python-tk 
```

works for me...


make sure u have ur repos enables and up to date... and try again

---

### Post by Spaceman9 on 2008-07-13
There's a great forum here for programmers [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by bcerge on 2008-07-13
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.5
E: Package python-tk has no installation candidate


: /

---

