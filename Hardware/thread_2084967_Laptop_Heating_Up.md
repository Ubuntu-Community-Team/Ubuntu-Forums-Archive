---
title: "Laptop Heating Up"
date: 2012-11-17
forum: Hardware
---

### Post by trizcuit on 2012-11-17
I've been noticing on my HP Pavilion m6-1045dx that its been overheating on the left corner side of my computer. I've installed everything imaginable spent countless hours on end looking through google. I'm not quiet sure what the problem is.

The problem doesn't seem persistent while I use windows 7 and the temps are low but once going over to Ubuntu after some use it seems to average at a hotter temperature and its uncomfortable to place wrist anywhere near it.

I'm up for trying _**anything**_ any help is appreciated. I'd like to move to Ubuntu fully.


Specs of computer:
64bit
8gb ram
core i5
Intel HD Graphics 4000
ivy bridge

Thanks!

---

### Post by ranger1021994 on 2012-11-17
I guess you might have CPU-intensive processes running in Ubuntu.
Check for such guzzlers by "top"

[Open terminal and type "top"
 without quotes]
Kill useless processes

---

### Post by trizcuit on 2012-11-17
> **ranger1021994 said:**
> I guess you might have CPU-intensive processes running in Ubuntu.
Check for such guzzlers by "top"

[Open terminal and type "top"
 without quotes]
Kill useless processes

All that runs is Chrome or Firefox. This happens on other linux distro's as well. Don't know if its incompatible hardware in my laptop or what.

---

### Post by holiday on 2012-11-17
You could check for new drivers. 

In 10.04, that is System.Administration.Hardware Drivers. 

Maybe someone knows where that is in 12.n. 

My laptop ran its fans high continuously until I did that.

---

### Post by trizcuit on 2012-11-18
> **holiday said:**
> You could check for new drivers. 

In 10.04, that is System.Administration.Hardware Drivers. 

Maybe someone knows where that is in 12.n. 

My laptop ran its fans high continuously until I did that.


Hardware drivers doesn't display any drivers for me to activate. Wish it did. I'd love to figure out what's causing this problem.

---

### Post by typhoon_tip on 2012-11-19
Start by posting the full output of (edit: do it when the computer seems HOT !):

```
sensors
```

---

