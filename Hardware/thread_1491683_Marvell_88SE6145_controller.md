---
title: "Marvell 88SE6145 controller"
date: 2010-05-23
forum: Hardware
---

### Post by amorangi on 2010-05-23
A continuation of this thread [http://ubuntuforums.org/showthread.php?t=507061&highlight=88SE6145]("http://ubuntuforums.org/showthread.php?t=507061&highlight=88SE6145") it appears the Marvell 88SE6145 controller problem has still not been resolved. Running 10.04 I still only get 2 HDDs or ports showing up off this controller, despite the fact there are 3 ports. Any ideas on a fix?

---

### Post by |Eric| on 2011-06-28
the problem is the module witch comes with linux 
only thing they need is to compile the freaken driver as a proprietary driver  (you can get the source free from [www.asus.com](www.asus.com) )

im too lazy to do it and so it seams for many ppl 
all they realy need is to add the freaken struct / variables 
to macth 4 drives instead of 2 thats it ... 

i successfully compiled the driver module many times and you can load it as teinted 
 
it would be real nice to have a .deb package that you can install precompiled !

---

