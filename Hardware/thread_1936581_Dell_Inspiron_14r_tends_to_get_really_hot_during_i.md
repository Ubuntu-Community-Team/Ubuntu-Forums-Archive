---
title: "Dell Inspiron 14r tends to get really hot during idle"
date: 2012-03-06
forum: Hardware
---

### Post by Xanza on 2012-03-06
I'm running Xubuntu 11.10 64bits and even during idle it's blowing out alot of air which to me would relate to the system heating up. What can I do to address this? 

Running 3.0.0-16 kernel
Intel i3 2.1Ghz Sandy Bridge with Intel HD 3000 Graphics
6GB RAM

---

### Post by peyu on 2012-03-06
Hi Xanza,
at least you can try to see if you have heavy processes running, with the monitoring application in xfce if it exists, or in a terminal with top

---

### Post by Xanza on 2012-03-07
Nothing's hogging up processes. CPU usage is at 3-6% while memory is at 8-12%

---

### Post by peyu on 2012-03-07
Did you try to check the cpu temperature ?
Or to limit the cpu frequency with some applet (gnome applet for cpu monitoring is able to do it, but I don't know if it exists in xfce)

---

### Post by Mark Phelps on 2012-03-09
It's a problem with the recent Linux kernels.  More info on this below:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

There have been CLAIMS that his has been fixed in 12.04, but I've recently seen some threads where folks installed the Beta to test this out -- and saw no improvement in their overheating problem.

---

