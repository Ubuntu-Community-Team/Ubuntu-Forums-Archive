---
title: "How to determine video hardware"
date: 2013-03-11
forum: Hardware
---

### Post by coolecho on 2013-03-11
Hello, I am running Ubuntu 10.04 on a Kontron ETXexpress COM express board. I have a ACER S232HL monitor and it can display max of 800X600. Is it possible to query the hardware to see what video hardware it has? I think I need to look for the driver for the video on this board.

---

### Post by slickymaster on 2013-03-11
There are a few ways of finding out what the graphics device you have. If you just want Make/Model then i'd recommend running from the terminal:
```
lspci | grep VGA
```
That will list the PCI devices attached and 'grep' VGA - which will remove all lines that do not contain the line 'VGA'.

Or, to a thorough detailed description:
```
lspci -vvnn | grep VGA
```

---

### Post by coolecho on 2013-03-15
Thank You for the help!

---

