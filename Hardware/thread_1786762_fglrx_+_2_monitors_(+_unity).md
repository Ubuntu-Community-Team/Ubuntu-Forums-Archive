---
title: "fglrx + 2 monitors (+ unity)"
date: 2011-06-20
forum: Hardware
---

### Post by rellai on 2011-06-20
We have Ubuntu 11.04 with the driver fglrx 11.05
At first we have had 10.10 with the driver fglrx from the repository
I have installed the driver from the site – but the computer became to work very slowly (the first driver with the correction thearing), in spite of that fact that all the installation are minimum. When I turned on the second monitor it was impossible to work. I decided to update the operational system to Ubuntu 11.04, but the problem was remained. After updating the drivers mesa appeared, I decided to install the drivers from the repository fglrx, the slowly work returned. I decided to update the operational system to the version 10.05. 
I can’t to develop a speed, to see the films even with the bad quality…
```
rellai@first:~$ glxinfo | grep OpenGL
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5570
OpenGL version string: 4.1.10665 Compatibility Profile Context
OpenGL shading language version string: 4.10
OpenGL extensions:
rellai@first:~$ 
```
I have one more problem:  the left panel Unity is located on my TV-set , in spite of the location of the TV-set (right or left), the panel  is always on it, is it possible to correct it?

---

### Post by sikander3786 on 2011-06-20
For the slowness issue, this might help.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

For the TV-set and Unity Panel problem, the latest Unity 3.8.16 might fix it but it would be a bit dangerous to install as it is your production sort of PC.

[http://ubuntu4beginners.blogspot.com/2011/06/upgrade-to-new-unity-3816-bug-fixing.html](http://ubuntu4beginners.blogspot.com/2011/06/upgrade-to-new-unity-3816-bug-fixing.html)

---

### Post by rellai on 2011-06-20
[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

Sync to VBlank - I have this checkbox is disabled

---

### Post by rellai on 2011-06-21
On the first point - thank you very much , everything work fast!
On the second point . added ppa whith unity update - put version 03.08.14 .
03.08.16 he did not see

---

### Post by rellai on 2011-06-21
Put 8.3.16. When you restart the panel is still on TV. if the TV is left to reload, and then make the settings right. the panel is moved to the monitor. after a reboot everything returns (((

---

### Post by rellai on 2011-06-22
up

---

### Post by rellai on 2011-06-23
up

---

### Post by rellai on 2011-06-23
can somebody help me?

---

### Post by rellai on 2011-06-26
up

---

### Post by rellai on 2011-06-28
up

---

