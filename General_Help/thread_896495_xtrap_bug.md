---
title: "xtrap bug"
date: 2008-08-21
forum: General Help
---

### Post by boponfire on 2008-08-21
Hi, 

The test apps coming with XTrap don't work on my Ubuntu hardy.

```
ben@homer:~$ xtrapreset
Resetting Display:  :0.0 
xtrapreset: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
```

I get the same with xtrapstats, etc

I want to develop an application using libXTrap but I get the same error when I run it. 

I have seen many threads where people get this error when running games or JAVA apps, but the solutions described don't work for me...

Thanks in advance,

---

