---
title: "Mouse moving script"
date: 2008-08-28
forum: General Help
---

### Post by skipsbro on 2008-08-28
I was wondering if it is possible to make a script that moves the cursor randomly on the screen.

---

### Post by jpkotta on 2008-08-28
Get the XAutomation tools.
```
sudo aptitude install xautomation
```

My screen is 2560x960 pixels.
```
$ xdpyinfo | grep dimensions
  dimensions:    2560x1024 pixels (765x302 millimeters)

```

Random pointer move.
```
xte "mousemove $(($RANDOM % 2560)) $(($RANDOM % 1024))"

```
It probably doesn't matter for what you're doing, but the above is not quite uniformly random.  It slightly favors a rectangle in the upper left.

---

### Post by skipsbro on 2008-08-28
Well, if it keeps the mouse moving, that's all I need, thanks!

---

