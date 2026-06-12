---
title: "nvidia installer wo/ kernel source (custom kernel)"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by graysky on 2009-03-30
I have a custom kernel on my Intrepid box.  I noticed that if I delete the ~/linux-2.6.29 dir where I built my kernel-image and kernel-headers, the nvidia installer fails to run complaining that it can't find the source directory.  I think noticed that there are two symlinks in my /lib/modules/2.6.29-xeon64:

```
build -> /home/stuff/linux-2.6.29
source -> /home/stuff/linux-2.6.29
```

I changed them both to point to the headers in /usr/src but the nvidia installer still complained that it can't find the source.  What am I doing wrong?


```
build -> /usr/src/linux-headers-2.6.29-xeon64
source ->/usr/src/linux-headers-2.6.29-xeon64
```

---

### Post by samrat1985 on 2009-04-08
Hi!

Same problem here. But I had infact created
nvidia driver since my problem was that

build -> something else .. NOW CORRECTED
build -> /usr/src/linux-headers-`uname -r`

Now I uninstalled the driver & tried to 
reinstalled & the same problem even if 
link is corrected!!

Hope to find a solution.

PS: If you found out reply in this thread 
I am following it.

---

