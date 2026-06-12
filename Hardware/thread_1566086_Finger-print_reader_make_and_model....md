---
title: "Finger-print reader make and model..."
date: 2010-09-01
forum: Hardware
---

### Post by madmax.santana on 2010-09-01
Is there a way I can find out the make and model of my finger print reader. I do not use it with Ubuntu.

I was thinking about finding out the model and make of my device and downloading a datasheet to fiddle with it and maybe create a few software implementations for it in basic C/C++.

I can find out about my PCI devices by lspci... Do you have any idea which port might this reader be connected to and what would give away its tech specs?

---

### Post by madmax.santana on 2010-09-02
Hellooooo! Anybody there?

---

### Post by IcarusR on 2010-09-02
If it is on usb bus then in terminal

```
lsusb
```


Also have a look in the log files to see if there is any thing relevant there.

---

