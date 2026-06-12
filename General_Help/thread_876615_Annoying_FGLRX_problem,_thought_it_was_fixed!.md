---
title: "Annoying FGLRX problem, thought it was fixed!"
date: 2008-07-31
forum: General Help
---

### Post by rolandixor on 2008-07-31
Every time I run certain programs (except in the fail safe terminal), I get this:
```
(program goes here): ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.

```

I don't know how to solve it, and I was told that upgrading to catalyst 8.7 would solve the problem. It didn't. I can't run blender, Amdcccle, OpenOffice 3.0, or even fglrxinfo!

Does anyone else know how to solve this? Or should I just downgrade my driver (again?)

---

### Post by tuxxy on 2008-07-31
COuld be yet another ATI driver problem if thats what your using.

---

### Post by rolandixor on 2008-08-01
seems to work only sometimes, if I log out, it happens again.
I then have to restart to get it to work.

---

### Post by fermulator on 2008-09-07
I'm getting a similar error:

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7873 Release
```

amdcccle:
```
amdcccle: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Aborted
```

sudo aptitude search fglrx
```
p   fglrx-amdcccle                                   - Dummy package for easy transition                          
p   fglrx-amdcccle-envy                              - Dummy package for easy transition                          
id  fglrx-control                                    - Control panel for the ATI graphics accelerators            
p   fglrx-control-envy                               - Control panel for the ATI graphics accelerators            
v   fglrx-driver                                     -                                                            
v   fglrx-driver-dev                                 -                                                            
i A fglrx-kernel-source                              - Kernel module source for the ATI graphics accelerators     
p   fglrx-kernel-source-envy                         - ATI binary kernel module source                            
i   xorg-driver-fglrx                                - Video driver for the ATI graphics accelerators             
p   xorg-driver-fglrx-dev                            - Video driver for ATI graphics accelerators (devel files)   
p   xorg-driver-fglrx-dev-envy                       - Video driver for ATI graphics accelerators (devel files)   
p   xorg-driver-fglrx-envy                           - Video driver for ATI graphics accelerators  
```

---

### Post by fermulator on 2008-09-07
Just noticed that fglrx-amdcccle wasn't installed, so I installed it, still the same error.

---

### Post by hackerseraph on 2008-09-07
what does fglrx-amdcccle do? any benefits?

"p   fglrx-amdcccle                                   - Dummy package for easy transition   "

---

### Post by fermulator on 2008-09-07
honestly I'm not certain, it's obviously some sort of 'shell/wrapper' package.

Regardless though, amdcccle should REALLY work ... ;/  (unless someone can suggest an alternative GUI aticonfig?)

---

### Post by hackerseraph on 2008-09-09
have you ever tried using Envy to auto setup?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It works for every installation I have ever set up on one of my machines, laptops, or a friends machine; I highly recommend ^^

---

