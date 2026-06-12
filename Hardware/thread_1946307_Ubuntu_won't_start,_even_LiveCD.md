---
title: "Ubuntu won't start, even LiveCD"
date: 2012-03-24
forum: Hardware
---

### Post by conseil on 2012-03-24
Hello,
my friend tried to install Ubuntu on his machine:
```
Manufacturer:  Processor: Intel(R) Core(TM) i3 CPU 550 @ 3.20GHz (4 CPUs), ~4.4GHz Memory: CORSAIR VENGEANCE 4096MB RAM 1600Mhz Hard Drive: 2x 80 GB Video Card: NVIDIA GeForce GTX 550 Ti
```He tried 11.10 and 12.04 beta and he got this: [http://img706.imageshack.us/img706/6370/photo1wfm.jpg](http://img706.imageshack.us/img706/6370/photo1wfm.jpg)
I read he should use Ubuntu 10.04 and then update it. Unfortunately he got another error: [http://img190.imageshack.us/img190/874/photo2za.jpg](http://img190.imageshack.us/img190/874/photo2za.jpg)
At this messages computer freezes.

He tried to install it through wubi and run it as LiveCD. Without any result.

Could you help me?
Thank you.

---

### Post by brainwash on 2012-03-24
Hey,

looks like a problem related to the nvidia display driver (nouveau). Booting with the *nomodeset* parameter might help here.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Cheers!

---

### Post by conseil on 2012-03-25
Thank you very much for your reply.
It worked for LiveCD, but is there any way to set "nomodeset" to wubi?

---

### Post by brainwash on 2012-03-25
You can find the answer in the same thread I already linked:
[]("http://ubuntuforums.org/showpost.php?p=10089820&postcount=8")
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

Method 2 should work for Ubuntu 11.10 and 12.04.

---

### Post by conseil on 2012-04-03
Thank you very much, that solved my problem.

---

