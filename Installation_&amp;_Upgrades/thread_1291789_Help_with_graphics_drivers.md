---
title: "Help with graphics drivers"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by bigec on 2009-10-15
I recently installed Ubuntu home on an old computer of mine, HP pavilion a210n, but it is really laggy and slow. My guess is either I just need to add more ram since it only has 256mb or the driver for the integrated video card isn't installed yet, it has intel extreme graphics 845 chipset. Does anybody know if this is preinstalled with the latest version of Ubuntu or how I can install it?

---

### Post by dabl on 2009-10-15
Not exactly a "solution" perhaps, but here are some things to consider:

1. The appropriate Intel video driver should have been automatically installed -- you can check with ```
sudo lsmod
```

However, Linux  Intel graphics drivers have been a misery, lately -- there's a thread devoted to the topic here:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

2. Yes, your RAM is considerably below the recommended spec.  If you can double or triple it, it will run noticeably better.

3. Xubuntu, with the Xfce desktop, should perform noticeably better on such a limited platform.  Xfce is pretty easy to use.

4. Here's a good article on tuning marginal systems:

[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

Hope this helps.  :)

---

