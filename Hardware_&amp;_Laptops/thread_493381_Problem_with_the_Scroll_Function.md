---
title: "Problem with the Scroll Function"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by Majorix on 2007-07-05
I have a problem that bugs me.

I have a Synaptics Pointing Device on my laptop. Every other function is ok, but when it comes to scrolling using the rightmost part of the device, there are some problems, ie. I can only scroll using the 2mm or so of the rightmost part of the device. And I usually miss that part and try scrolling using the parts that are more to the left of it and as such the screen won't scroll.

Is there a fix for this you can think of? Any drivers I should install? Any configuration I should do?

Thanks for any help you can come up with :)

---

### Post by geraldm on 2007-07-05
man synaptics
It says that the pad is divided into sections, which can be reconfigured
in the shared memory that it runs in.  Change the parameters to your liking.

---

### Post by Majorix on 2007-07-06
Ok thanks for pointing me in the right direction :) Reading from there, I fixed the problem by typing this in terminal:
```
synclient RightEdge=800
```

The 800 part can be changed of course, but to me it seemed like a very reasonable parameter. Fyi, RightEdge defaulted to a 921 by me.

---

