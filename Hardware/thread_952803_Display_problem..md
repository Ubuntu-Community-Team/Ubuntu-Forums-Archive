---
title: "Display problem."
date: 2008-10-19
forum: Hardware
---

### Post by Mr0wyx on 2008-10-19
Hello!

I have problems with my Samsung 913N 19" monitor. In process when ubuntu is loading it turns black and shows little window on screen saying "Not Optimum mode Recommended Mode 1280x1024@60Hz" (monitor warning not ubuntu). This notification window appears in different loading stages. Sometimes where splash should be and sometimes when it loads and sometimes all the booting up. When I unplug and plug back in power cable from monitor it starts to work normal but until it changes resolution. When it changes same thing happens (black screen). I have tried to install graphics card drivers (nvidia 6600). And without driver. It does not make any difference. But when I install windows back on everything works ok.

---

### Post by cariboo on 2008-10-19
Assuming you are installing version 8.04, when you get your monitor working press Alt-F2 and type:

```
gksu displayconfig-gtk
```

This utility will allow you to set the resolution for your monitor.

Jim

---

