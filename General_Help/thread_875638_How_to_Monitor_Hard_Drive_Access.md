---
title: "How to Monitor Hard Drive Access?"
date: 2008-07-31
forum: General Help
---

### Post by dreikin on 2008-07-31
Does anyone know of a script or program to monitor and/or log hard drive accesses (over a fairly short period of time, of course)?  I want to see which programs are accessing the disc at certain times.

---

### Post by forger on 2008-07-31
This is to check the device status (sleeping,idle,active etc)
[http://ubuntuforums.org/showthread.php?t=172383](http://ubuntuforums.org/showthread.php?t=172383)

Finding out which process, no idea :( Do post back if you find out!

---

### Post by forger on 2008-07-31
maybe I found something:
[http://packages.ubuntu.com/hardy/inotify-tools](http://packages.ubuntu.com/hardy/inotify-tools)
[http://packages.ubuntu.com/hardy/libinotifytools0](http://packages.ubuntu.com/hardy/libinotifytools0)

> Inotify is a Linux kernel feature enabling user space programs to monitor parts of the filesystem in a efficient way. libinotifytools is a thin layer on top of the kernel interface which makes it easy to set up watches on many files at once, read events without having to deal with low-level I/O, and several utility functions for inotify- related string formatting 

Documentation:
[http://inotify.aiken.cz/?section=inotify&page=faq&lang=en](http://inotify.aiken.cz/?section=inotify&page=faq&lang=en)
> 
Q: Can I monitor executing a program?
Not directly. You can monitor accessing the executable file (IN_ACCESS) but not distinguish between reading and executing. There is possibility to examine procfs consecutively but it is not reliable. 

---

