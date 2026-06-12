---
title: "Hardware Detection"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by p252 on 2007-03-29
Hi all,

I am curious. . . I have Ubuntu 6.10 running on two laptops (Dell Inspirion 1300 and HP ZE4430US) and for the most part they run great (the HP runs a little warm though). However, I noticed most the hardware isn't necessarily detected though it is working. What I mean is, if I do a 'uname -a' it tells me I have an i686 but doesn't tell me what processor (did a man on 'uname' and it says it's because the the processor is unkown to the system). Also, In Device Manager, most hardware shows "unkown." Question is, is this normal for Ubuntu? If the hardware is unkown is it being run correctly? Most other distros I have tried at least pick up the processor types (my dell has a Intel Celeron M 1.6mhz and the Hp has a Mobile AMD Athalon XP 4) and usually the graphics cards (though supporting them is another matter).

Thanks

---

### Post by Jussi Kukkonen on 2007-03-29
I don't think uname knows much about anything... Use something like lshw to get some  actual data.

---

### Post by p252 on 2007-03-29
Awesome. That's a good command, thanks! That shows my hardware. Still don't know why Device Manager lists everything as unknown. . .

---

