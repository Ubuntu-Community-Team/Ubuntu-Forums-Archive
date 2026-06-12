---
title: "ATI 4870 fans setting ability?"
date: 2009-01-12
forum: Hardware
---

### Post by erdal123 on 2009-01-12
i have ati drivers installed in ubuntu
in windows in the same program i could sett the fanspeeds

buttttt there is not "OVERDRIVE' function in ubuntu, where you can regulate the fan speed manually

its so irritating because its videocard is on automatic and it runs at 60% instead of 30% which i always sett in windows

do i have the wrong driver?

secondary question: i heared someting about a program where i can run windows programs, if thats so why the trouble with alternative windows->lunix applications

---

### Post by nick09 on 2009-01-13
You can use Wine to run windows programs but it varies because Wine is built up from scratch, not from windows itself because of copyright I believe.

You can run atconfig in the terminal, but I don't know if that controls the fans(you can under-clock the graphics card though).

---

### Post by erdal123 on 2009-01-14
> **nick09 said:**
> You can use Wine to run windows programs but it varies because Wine is built up from scratch, not from windows itself because of copyright I believe.

You can run atconfig in the terminal, but I don't know if that controls the fans(you can under-clock the graphics card though).

after you installed "wine"

you just abble to install EXE files?

---

### Post by erdal123 on 2009-01-15
> **nick09 said:**
> You can use Wine to run windows programs but it varies because Wine is built up from scratch, not from windows itself because of copyright I believe.

You can run atconfig in the terminal, but I don't know if that controls the fans(you can under-clock the graphics card though).

its impossible to run device sofware with WiNe I DISCOVERED


DOES ANY ONE HAVE A ALTERNATIVE?

---

### Post by Yashiro on 2009-01-15
Press Alt+F2,
enter *aticonfig --pplib-cmd "set fanspeed 0 30"*

---

### Post by erdal123 on 2009-01-16
> **Yashiro said:**
> Press Alt+F2,
enter *aticonfig --pplib-cmd "set fanspeed 0 30"*

and how do i sett it back?

---

### Post by Yashiro on 2009-01-16
*aticonfig --pplib-cmd "set fanspeed 0 **30**"*

Log out or set a better value, 0 or -1 dunno I don't use it anymore.
The speed is not saved permanently anyway. So just log out.

---

