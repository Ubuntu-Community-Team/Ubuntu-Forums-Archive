---
title: "Intel 945 Graphics Card Issues (Direct Rendering Problems)"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by Espionage724 on 2007-06-11
I have a Intel 945 Graphics Card. Sometimes when I open certain programs such as Beryl or another program that uses OpenGL, the direct rendering will turn off and if I am using a desktop manager it would make my computer unuseable. It only happens sometimes though but is there a fix for this?

---

### Post by ramjet_1953 on 2007-06-11
Which driver do you have installed?

I tried the newer [COLOR="Blue"]xserver-xorg-video-intel[/COLOR] driver and it gave me problems and even crashed X, when a program dynamically changed the screen resolution.

So I got rid of it and re-installed the [COLOR="Blue"]i810 driver[/COLOR] and configured it with [COLOR="Blue"]915resolution[/COLOR].

No more problems.

There is more information here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger :cool:

---

