---
title: "Ubuntu start up problems, get multicoloured mess"
date: 2008-10-02
forum: General Help
---

### Post by fallenstar on 2008-10-02
Since I installed Ubuntu Studio, when I start it up, it becomes a multicoloured mess, with coloured lines all over the screen, then it goes black, then grey, eventually giving up and staying black. To start Ubuntu, I have to load rescue mode, then choose resume start up, and it starts fine.

Know the disk's fine, md5sum checks, installed the other day from it, no problem.


Thanks in advance!

---

### Post by Sef on 2008-10-02
1) What graphics card do you have?   

2) Do you have onboard graphics or an extra card around?  If so, try them.

---

### Post by fallenstar on 2008-10-02
I've got a Dell Inspiron 1525 laptop, no other graphics controller possible

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Cheers :)

---

### Post by fallenstar on 2008-10-04
Just in case anyone ever has the same problem, it's that the graphics card drivers haven't installed correctly, resulting in freezing and funny graphics during start up, and the inability to do any effects (Alt + F2, and left or right curser give a box, rather than effects like sliding or exploding, good indication that graphics card drivers haven't installed properly).

Install new drivers from System/Administration/Hardware Drivers, enable the graphics card driver and it will install the software. Graphics card works post restart.

---

