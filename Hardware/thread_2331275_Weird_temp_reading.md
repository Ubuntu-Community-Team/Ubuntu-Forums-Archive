---
title: "Weird temp reading"
date: 2016-07-20
forum: Hardware
---

### Post by imballinger on 2016-07-20
I am getting this in my system logs

20/07/2016 10:19    Server    kernel    [419277.773237] nouveau 0000:01:00.0: therm: temperature (106 C) hit the 'critical' threshold


I take it that it's a wrong reading?

It is listed as "temp 1" whatever that refers too

---

### Post by TheFu on 2016-07-20
nouveau - is the GPU driver, so I would **guess** it is the GPU overheating.  I would look at getting better case cooling.  Are all the other temps high too?  My CPU is at 41.8 degC now and 104.0 is the "critical" warning, but I've never seen higher than 49 degC on it.  The GPU is built-into the CPU on this system.

---

### Post by imballinger on 2016-07-20
Thanks for pointing me in the right direction, Looked and noticed the graphics card fan has stopped working, I'm surprised it didn't melt with how hot it was :o

---

