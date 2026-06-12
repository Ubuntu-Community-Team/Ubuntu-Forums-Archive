---
title: "[SOLVED] My only desktop resolution is 800x600"
date: 2008-09-29
forum: General Help
---

### Post by tmbt on 2008-09-29
Hi guys,
as topic says.
I have Ubuntu 8.04
I installed openchrome driver succesfully but now i have only 800x600 and 640x480 to choose.

I will attach my xorg.conf.
Please give a look to check if something is wrong.

Thanks in advance

---

### Post by dagoss on 2008-09-29
Have you tried logging in without X and running:```
sudo dpkg-reconfigure -phigh xserver-xorg
```?

---

### Post by TheLions on 2008-09-29
also there was some cases in which removing file xorg.conf would work, but i havent tried that, so on your own risk. 
**[COLOR="Red"][SIZE="4"]also backup everything you need before this!![/SIZE][/COLOR]**

[http://ubuntuforums.org/showthread.php?p=5849703#post5849703](http://ubuntuforums.org/showthread.php?p=5849703#post5849703) post #6

---

### Post by tmbt on 2008-09-29
i'm sorry but both your suggestions was not usefull.
If i remove the xorg.conf it just replace it with a new tiny version.
If i run sudo dpkg-reconfigure -phigh xserver-xorg
i get a new xorg.conf exactly the same the one i attached before.

I have to tell u also that when i tried to install ubuntu 8.04 i got problems with my video-card driver so i use the boot option F4 or F5 to do a safe graphic boot.
Could be the problem ??

Thx

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by tmbt on 2008-09-30
I solved the problem.
I was missing :

VertRefresh 60
HorizSync 31.5-90

in the xorg.conf under Section "Monitor".
I added this 2 row and restart X.
Now everything work fine.

Thx to all for the help

---

