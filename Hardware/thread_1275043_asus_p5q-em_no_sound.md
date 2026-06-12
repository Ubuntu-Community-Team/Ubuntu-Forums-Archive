---
title: "asus p5q-em no sound"
date: 2009-09-25
forum: Hardware
---

### Post by st4th1s on 2009-09-25
i recently bought an asus p5q-em motherboard and i installed ubuntu 9.04(x64). everything is ok except from the sound (i have to mention that i use ubuntu for 6 months, so i do not know a lot about them...). 
in volume control window -> Device i can select between HDA Intel (Alsa mixer) and Realtek ALC1200(OSS Mixer). both of them have no result... 
I have tried a lot of suggetions that i found in google but nothing worked for me...
please help...

tnx.

IT FINALLY WORKS....

---

### Post by maxmartin on 2009-09-26
What did you do to get it working? I am on the same board and experiencing the same problem.

EDIT: Nevermind, the solution posted on [this thread]("http://ubuntuforums.org/showthread.php?t=939198") involving the change to alsa-base.conf worked for me.

---

### Post by st4th1s on 2009-09-27
i updated kernel to 2.6.30 and it worked...

---

