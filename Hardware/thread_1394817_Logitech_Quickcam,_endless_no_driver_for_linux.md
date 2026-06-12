---
title: "Logitech Quickcam, endless no driver for linux ?"
date: 2010-01-31
forum: Hardware
---

### Post by frenchn00b on 2010-01-31
Hello

After reading this thread and using a 2.6.32 kernel it seems that no solution could have been given to such common types of webcam.

Reading this thread, seems that no one will make a new driver, working, instread of machaard.
[http://ubuntuforums.org/showthread.php?t=205782](http://ubuntuforums.org/showthread.php?t=205782)
 Compiling is not working, definitely, we need a launchpad for a new and better driver !

I found out that is a hack to get one single frame.
this way is working
```
 scanimage -d "v4l:/dev/video0" --mode color > test.ppm
 convert test.ppm test.jpg
```

---

