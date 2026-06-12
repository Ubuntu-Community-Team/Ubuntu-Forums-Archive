---
title: "yab problem"
date: 2008-10-24
forum: General Help
---

### Post by 24dhruv on 2008-10-24
i want to install yab on my ubuntu8.04(64 bit edition) and i have executed this command and found  this i cant understand the problem please help 


```
dhruv@dhruv-laptop:~/Desktop/icon packs/yab-0.0.2$ ./yab.py --nautilus
Traceback (most recent call last):
  File "./yab.py", line 48, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'
dhruv@dhruv-laptop:~/Desktop/icon packs/yab-0.0.2$ 

```

---

