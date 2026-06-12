---
title: "Detailed app for Hardware ???"
date: 2010-06-13
forum: Hardware
---

### Post by smittie46 on 2010-06-13
This is answered I know but I am having a tough time seeing if this is available a app that will list your hardware components,like a device manager New to Ubuntu just love it and curious if there is drivers for my core I7 3.06 6gig DDR3 ATI 4830 just like a cpu-z for linux everything is working great just like to see Hardware list Thanks alot

---

### Post by bruno9779 on 2010-06-13
From the command line there is plenty.

```
lshw lsusb lspci
```

and more. I dunno about GUI clients

---

### Post by cascade9 on 2010-06-13
There are drivers for the ATI 4830- if you dont have them installed then go-

System-> Administration-> Hardware Drivers

Hardinfo for a GUI that shows you installed hardware (and a lot of other thngs). Nowhere near as much information as lshw shows though. 

IIRC is renamed "system profiler and benchmark" in the menu list..dont be fooled, it is a bad benchmarker, if you really want to benchmark get the phonoix test suite.

---

### Post by smittie46 on 2010-06-13
Thanks I am just getting use to Terminal and I appreciate the help Thank you very much

---

### Post by cascade9 on 2010-06-13
No problem. ;) 

Good luck with linux and I hope you enjoy it ;)

---

