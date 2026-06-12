---
title: "Different kind of freeze Hardy Heron Freezes"
date: 2008-09-05
forum: General Help
---

### Post by xXZeroXx on 2008-09-05
Well, there are a lot of posts about this, but my situation is a little more different, I'll explain:
After around 5 or 6 hours, the screen starts getting strange colors, some kind of rectangles of many colors (pink, green, yellow) and then it freezes, when I first started to use ubuntu it freezed with no reason, but, when I eliminated powernowd, it worked excellent, lately, I¡ve been messing with ALSA, PulseAudio, and the Sound and Video, I don't know if this has something to do with this, because it didn't happened before.
Please Help
Thanks!!

---

### Post by wolfen69 on 2008-09-05
> **xXZeroXx said:**
> 
After around 5 or 6 hours, the screen starts getting strange colors, some kind of rectangles of many colors (pink, green, yellow) and then it freezes

sounds like your video card may be overheating.

---

### Post by xXZeroXx on 2008-09-06
No, now it freezes every hour, I think I messed something up, what should I do?:confused:

---

### Post by cariboo on 2008-09-06
It does sound like your video card is defective. If you have another video card laying around, give it a try.

Jim

---

### Post by xXZeroXx on 2008-09-06
No, I don't have any other video card, I was thinking about reinstalling ubuntu and seeing what happens, what do you think?
By the way, how much life is a video card supposed to have for, like 3 or 4 years?

EDIT: Just after I replied, the system froze, is there any log file where I can look at.
PD: It is not a complete freeze, because, I could reboot with ALT + PRINT SCREEN + R E I S U B, but if don't do that, I have to hard reboot my pc.

---

### Post by xXZeroXx on 2008-09-06
My screen just shows loads of weird colours/patterns. I think it is related to X

Well, this what I got from terminal with the command "top":


PID   USER    PR  NI VIRT  RES  SHR  S %CPU %MEM TIME+   COMMAND            
6725 xxzeroxx 20  0  3080  276m 9832 S 47   7.5  5:02.73 npviewer.bin
6763 xxzeroxx 20  0  45090 18m 86632 S 15   1.8  0:27.67 transmission
5269 root     20  0  238m  80m  19m  R  3   8.6  6:30.50 xorg
5823 xxzeroxx 20  0  209m  116m 22m  S  3   18.6 2:31.33 firefox
5685 xxzeroxx 20  0  22720 15m  5872 S  1   1.5  0:21.78 compiz.real
5765 xxzeroxx 20  0  25864 11m  8288 S  1   1.2  0:01.86 nm-applet
5849 xxzeroxx 20  0  66424 19m  10m  S  1   1.9  0:02.22 gnome-terminal


The rest of the processes had just 0's, so I think they are not important,
how did I get this? well, I ran the command top on terminal and waited until it froze up, once it was frozen, I started to write everything that was in there, and then I wrote it here.

Please help me, I don't know what to do.

---

