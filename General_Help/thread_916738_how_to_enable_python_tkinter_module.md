---
title: "how to enable python tkinter module?"
date: 2008-09-11
forum: General Help
---

### Post by jingqi on 2008-09-11
The Tkinter module needs to be enabled when I install sketcil. Python 2.5 had been installed on my Ubuntu, when I test whether the tkinter is active or not, the following error jumped out, 
jqduan@jqduan-laptop:~/Desktop/Python-2.5.2/Demo/tkinter/guido$ python hello.py
Traceback (most recent call last):
  File "hello.py", line 4, in ?
    from Tkinter import *
  File "/usr/local/lib/python2.4/lib-tk/Tkinter.py", line 38, in ?
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: libtk.so.0: cannot open shared object file: No such file or directory

Therefore I think my tkinter need enabling.As a new to ubuntu, however, I don't know how to enable it. Can anyone help me?

---

### Post by pansz on 2008-09-11
sudo apt-get install python-tk

---

### Post by jingqi on 2008-09-11
After intalling the python-tk, the following error still exists

jqduan@jqduan-laptop:~/Desktop/Python-2.5.2/Demo/tkinter/guido$ python hello.py
Traceback (most recent call last):
  File "hello.py", line 4, in ?
    from Tkinter import *
  File "/usr/local/lib/python2.4/lib-tk/Tkinter.py", line 38, in ?
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: libtk.so.0: cannot open shared object file: No such file or directory

Thanks anyway.

---

### Post by pansz on 2008-09-18
It seems that you have a compiled-from-source version of Python 2.4, and the Demo you're running is from Python 2.5

Ubuntu does not work with that well. try the following do disable your customized version of python:

sudo rm -f /usr/local/bin/python
sudo aptitude reinstall python python2.5
sudo aptitude reinstall python-tk

---

