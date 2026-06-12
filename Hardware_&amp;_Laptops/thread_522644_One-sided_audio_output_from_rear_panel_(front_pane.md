---
title: "One-sided audio output from rear panel (front panel perfect)"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by Giggity on 2007-08-10
Hi.  I doubt this has anything to do with Ubuntu, but I figure since y'all are so smart about computer stuff, and have been very helpful in the past...

I recently got the front-panel audio hooked up so I can listen through my headphones via the front panel (rather than use a Y-splitter on the rear output jack).  Since then, the front output works perfectly with equal balance.  However, the speakers via the back panel exhibit very imbalanced audio.  The left speaker puts out the expected volume of sound, but the right speaker is very very quiet!

This happened only since I connected the front-panel audio to the motherboard.  Does anyone know what might be going on?  My motherboard is an ECS nForce4M-A.

Thanks for all of your past assistance.

** I'm sorry... I posted this in the wrong forum.  It should have been Multimedia and Video.  If necessary, I hope someone can move it.

---

### Post by fredj on 2007-08-10
Its not an unknown problem but we need to know which sound chip you are using.
Open a terminal and type
sudo cat /proc/asound/card0/codec\#*
The first line of the output from this should contain the name of your sound chip. If you don't
get any output then look in your motherboard manual or post again. 
In general its good to include in your post the version of Ubuntu and either the make of your
computer or the model of the motherboard you are using.

---

### Post by Giggity on 2007-08-11
Here you go:

Version:  Ubuntu 7.04
Mobo:  ECS nForce4M-A

Unfortunately, I got nothing from the shell command:

```
rob@rcr-desktop:~$ sudo cat /proc/asound/card0/codec\#*
Password:
cat: /proc/asound/card0/codec#*: No such file or directory
rob@rcr-desktop:~$ 
```

Thanks for your help, and I'm sorry I didn't make the needed info more clear.  I had it kinda embedded in my other statements, making it hard to notice.

---

### Post by Giggity on 2007-08-12
I guess this thread got lost to lower pages overnight... wondering if anyone has any input.  Thanks!  :)

---

### Post by Giggity on 2007-11-20
Does anyone have any advice for this problem?  I've moved onto 7.10 and still have to unplug my headphones and plug in my speakers to the front panel to get stereo sound.

---

