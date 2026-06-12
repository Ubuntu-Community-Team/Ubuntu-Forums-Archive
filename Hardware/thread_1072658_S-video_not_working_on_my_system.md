---
title: "S-video not working on my system"
date: 2009-02-17
forum: Hardware
---

### Post by ice_noname on 2009-02-17
hey i have a problem with my s-video output....
i am runing ubuntu 8.10 on a lenovo 3000 N100,the problem is that wen i connect it to my tv nothing comes up, its just as if the port is not active at all!!! I really need it for my work at UNI and i don't wana go back to windows(HELL NO) so if anyone can help me im really going to appreciate it !! tnx;)

---

### Post by nixscripter on 2009-02-17
What kind of video card does it have? Some drivers, such as Intel's, are notorious for ignoring things like that. You can run ```
lspci | grep -i graphic
``` in the Terminal to get an idea.

---

### Post by ice_noname on 2009-02-18
hmm i ran the command and yes its intel !! this is the output i get!!

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by nixscripter on 2009-02-18
I'm sorry to say it, but I've got a similar on board controller, and it's well known that it doesn't suppor S-Video. :(

---

### Post by ice_noname on 2009-02-18
hmm thats bad!! ohh well thnx for the help anw , much appreciated!!

---

