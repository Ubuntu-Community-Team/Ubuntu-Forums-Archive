---
title: "ThinkPad T61 UltraNav"
date: 2010-02-28
forum: Hardware
---

### Post by Kerma on 2010-02-28
Hi all you geeks out there!

I've got a Lenovo ThinkPad T61 laptop, and I'm using Ubuntu 9.10. Since I installed 9.10 have everything worked fine, except one thing, ThinkPad's UltraNav scroll function. 

Picture of ThinkPad's UltraNav can you find [here.]("http://www.thinkpads.com/wp-content/gallery/thinkpad-t400s/lenovo_thinkpad_t400s_ultranav.jpg")

Anyways, in the previous versions, when the xorg.conf still existed did you just have to change 2 lines in it to make the scroll function work. 

Guide for previous Ubuntu versions can you find [here.]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.04_on_a_ThinkPad_X41")

Well now I'm sitting here, and don't have a clue how to make it work.

Does anyone know how to make ThinkPad's UltraNav scroll function work in Ubuntu 9.10?

Cheers.

---

### Post by era86 on 2010-03-08
See my signature

---

### Post by DomesDKG on 2010-03-10
I'm having the exact same problem, on a T400.  I looked through the thinkpad forums in your signature briefly but couldn't find the answer.

Anyone know how to solve this issue?

---

### Post by era86 on 2010-03-10
> **DomesDKG said:**
> I'm having the exact same problem, on a T400.  I looked through the thinkpad forums in your signature briefly but couldn't find the answer.

Anyone know how to solve this issue?

Have you looked here?  [http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400)

I don't think you modify the xorg.conf anymore.  I've noticed the later versions of Ubuntu tell you to modify/create an fdi file and restart HAL.

---

### Post by tgalati4 on 2010-03-10
configure-trackpoint works nicely on Jaunty with a thinkpad t43p.

---

### Post by DomesDKG on 2010-03-10
Thanks! it works great now, just followed these instructions:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

---

### Post by DomesDKG on 2010-04-30
This no londer works in Ubuntu 10.4, has anyone come up with a solution?

---

