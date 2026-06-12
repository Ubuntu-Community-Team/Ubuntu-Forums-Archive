---
title: "Logitech MX Revolution - setting up the scroll button to be a double click"
date: 2009-06-02
forum: Hardware
---

### Post by ardashla on 2009-06-02
Hi guys

I have a Logitech MX Revolution mouse and want to setup the middle scroll button to act as a double click - like it does on any normal 3 button mouse.

Does anyone have any ideas? Or shall i go back to the old school mouse. 

thanks
Vasco

---

### Post by ardashla on 2009-06-02
By the way i have 9.04 installed

Vasco

---

### Post by koshari on 2009-06-03
You can do what i did and re-allocate left tilt (button 6) as scrollwheel click (button 2) by placing this code-

```
pointer = 1 6 3 4 5 2 7 8 9 10 11 12 13 14 15 16
```

in a file called ```
/home/user/.xmapmod
``` which effectively swaps the functionality of the non existent button2 (which instead changes the function from ratcheting to freespinning wheel on these mice) with the left wheel tilt binding.

alternatively this thread may be worth a read, 

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

btnx is a very powerful app with regard to the revolution mouse

---

### Post by ardashla on 2009-06-04
ill give it a go, thanks

Vasco

---

