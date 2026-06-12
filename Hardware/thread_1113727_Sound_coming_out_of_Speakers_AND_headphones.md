---
title: "Sound coming out of Speakers AND headphones"
date: 2009-04-01
forum: Hardware
---

### Post by Marcham89 on 2009-04-01
I don't know why but the sound is coming out of both the speakers and headphones. I have a Dell Studio XPS 16 notebook. It has three audio jacks. Two headphone jacks and one mic jack. If I plug something into the first jack there is no sound coming from either the headphones or speakers. If I plug something into the second jack sound comes from both the headphones and the speakers. Any help is very appreciated. Thanks. :)

---

### Post by Marcham89 on 2009-04-03
Anyone?? Save me from windows....

---

### Post by Blahah on 2009-04-03
This sounds like a hardware problem common to Dell laptops. There is a switch inside the headphone socket. When the jack is inserted, the switch should depress, cutting power to the speakers. If the switch breaks, the sound will come out of both the speakers and the headphones.

If your laptop is still under warranty, get it repaired.

---

### Post by Marcham89 on 2009-04-03
I don't think that's the issue. The headphones work perfect in windows.

---

### Post by aniketvb on 2009-04-04
have a look here

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

I have a studio XPS 13, and adding correct model parameter helped me solve the problem as mentioned in the thread.

---

### Post by Marcham89 on 2009-04-04
Okay great I'll try that!

---

### Post by Marcham89 on 2009-04-07
Fixed! I upgraded to 9.04 and the issue disappeared.

---

### Post by aniketvb on 2009-04-08
Thats nice, 9.04 uses the upgraded version of alsa-driver which solved the issue. In my 8.10 install, I manually installed alsa-driver from svn to solve it, alongwith the correct model parameter

@blahah, please make sure what you are posting before you do so!! hardware switches depressing to cut power etc are a thing of distant past!! Please please take some trouble to verify you facts before posting.

---

