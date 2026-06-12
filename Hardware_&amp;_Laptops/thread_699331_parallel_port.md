---
title: "parallel port"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by bschleusner on 2008-02-17
I am using pyparallel under python, and when ever I type this:

```
import parallel
p = parallel.Parallel()
```

I get:

```
Traceback (most recent call last):
  File "/home/brad/projects/parallel.py", line 1, in <module>
    import parallel
  File "/home/brad/projects/parallel.py", line 3, in <module>
    p = parallel.Parallel()     #open LPT1
AttributeError: 'module' object has no attribute 'Parallel'
```

I tried it as root and a regular user, and it does the same thing. Any suggestions?

---

### Post by bschleusner on 2008-02-17
ok, it gets worse. Now I am getting this as my error (don't know why?)....

```
>>> import parallel
>>> p = parallel.Parallel()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 189, in __init__
    self.setDataDir(1)
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 509, in setDataDir
    self.PPDATADIR(out)
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 458, in PPDATADIR
    fcntl.ioctl(self._fd, PPDATADIR, msg)
IOError: [Errno 22] Invalid argument
```

---

