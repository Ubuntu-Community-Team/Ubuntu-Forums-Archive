---
title: "Intel GMA 3600 Problem with Temporary Solution Script"
date: 2012-05-16
forum: Hardware
---

### Post by BillyCMcGee on 2012-05-16
Hello everyone!

I am new here and I hope I can help some people out that are having the same issue that I am having. 

I just purchased a new netbook (Gateway LT4004u) to run Ubuntu and everything works great except there is no way at all to adjust the brightness. The hotkeys do not work, and there is no option to adjust the brightness in the Brightness and Lock system setting. 

There is nothing listed under /sys/class/backlight so something is wrong. I have been reading around and it looks like the GMA 3600 is not yet supported. 

I'm not sure if I just have sensitive eyes, but I could not deal with the brightness being at full blast all the time, and neither could my battery so I just came up with a quick python script that will adjust the brightness for you. There are 6 presets and the option to enter your own value in so you can mess around with it until you find one you like.

I hope this is in the right place, and I hope someone finds this helpful. I am new to all of this stuff but the python script works (at least it does for me) so I hope this helps!:P

Just run the script from a terminal (must have super user privileges) and follow the on screen instructions. Feel free to share this with anyone, I don't really care. 

BillyCMcGee

---

### Post by easydo on 2012-06-04
Thanks buddy. A little more roundabout than a function key, but I think you just cured my two month old headache. Now if I can just get the scroll on my touchpad to work, I'll be set.

---

### Post by BillyCMcGee on 2012-06-08
> **easydo said:**
> Thanks buddy. A little more roundabout than a function key, but I think you just cured my two month old headache. Now if I can just get the scroll on my touchpad to work, I'll be set.

Glad I could help someone out! :D Hopefully Intel will release some support for their product so we could just go back to using the function keys.

---

