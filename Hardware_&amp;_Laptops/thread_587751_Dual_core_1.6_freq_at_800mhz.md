---
title: "Dual core 1.6 freq at 800mhz"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by jkarma on 2007-10-23
This is my first official switch to Linux and after installing conky and configing it to my liking I've noticed that it reads my cpu freq at 800 mhz. I have a 1.6 dual core so I'm wondering how to check that I am taking advantage of both. I assume that in sys monitor cpu1 and cpu2 are each core right? How do I get this to register in conky. 

And how can I adjust my webcam colors. I see that gspca is compatible with the camera but camorama doesn't allow me to use any adjustments and the 1.3 mega pixel advertised is about as high quality as the poorest of camera phones. I've seen it in a windows environment and it looked great.

---

### Post by Linicks on 2007-10-23
The CPU's step.

Do a:

cat /proc/cpuinfo

you should see 2 CPU.

Now run (in another console):

glxgears

and then look at /proc/cpuinfo again.

I think you will find both are now running full chat.

Nick

---

### Post by shad0w_walker on 2007-10-23
The odds are that your dualcore is capable of scaling down its frequency when its idle and automatically step it  backup when it is needed.

---

