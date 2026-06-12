---
title: "A little help, please?"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by solitary man on 2007-10-30
Hello

I have a minor problem with my Radeon on Ubuntu. I Have tried to use the new ati drivers, but somewhere in the process I might have done something wrong. Probaly, seeing as I'm very new to Linux.
So I was wondering if anyone could help me getting things back to "normal", if such a thing is possible. Or maybe tell me where I can find some sort of guide.

Thanks 
Rasmus

---

### Post by pay on 2007-10-30
What problem are you having?

---

### Post by taurus on 2007-10-30
Are you having problems with X?

---

### Post by solitary man on 2007-10-30
Well, I'm not entirely sure, I embarrassed to admit. 
Not surprising compiz, does not work, but I'm quite used to that. :)
I'm trying neither does Amarok, I just discovered? So I'm a bit puzzled. 
I'm trying to go back to using the unrestricted drivers, but I think I may have removed them. Anyway, I can't see what drivers I'm using since neither glxinfo or fglrxinfo works.  Both turns out:  
"error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory". 
Actually, so does amarok. I dont know if this helps any at all?

---

### Post by taurus on 2007-10-30
Which release are you running right now?  Are you using KDE?

---

### Post by solitary man on 2007-10-30
I'm using Ubuntu 7.10.

---

### Post by pay on 2007-10-30
ahhh. i think i know whats wrong. Try```
cd /usr/lib
sudo ln -s libGL.so libGL.so.1
```

---

