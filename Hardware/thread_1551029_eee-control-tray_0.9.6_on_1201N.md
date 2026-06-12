---
title: "eee-control-tray 0.9.6 on 1201N"
date: 2010-08-11
forum: Hardware
---

### Post by uniontroublemaker on 2010-08-11
Has anyone been successful getting eee-control-tray 0.9.6 to run on EEE 1201N?

---

### Post by Chillawowa on 2010-09-01
Hi, I'm runing a 1201N with 64 bit kubuntu 10.04. When I try to start eee-control-daemon or eee-control-tray I get an error: 

```
Traceback (most recent call last):
  File "/usr/bin/eee-control-daemon", line 25, in <module>
    import EeeControl.actions
  File "/usr/lib/python2.6/dist-packages/EeeControl/actions.py", line 25, in <module>
    import ioport
ImportError: /usr/lib/python2.6/dist-packages/EeeControl/ioport.so: wrong ELF class: ELFCLASS32

```

Does this have something to do with 32 and 64 bit python? And I have only seen this problem once before [here]("http://forum.ubuntu-it.org/index.php?topic=398892.msg3103309;topicseen")

---

### Post by uniontroublemaker on 2010-10-21
So there is a solution.  Remove eee-control and install Jupiter  [http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)  , along with the eee file.  So far works great.

---

### Post by ottabaub on 2011-02-14
> **uniontroublemaker said:**
> So there is a solution.  Remove eee-control and install Jupiter  [http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)  , along with the eee file.  So far works great.

Yes, maybe, but that's an RPM which Ubuntu doesn't recognize. Not much good for people running Ubuntu.

---

