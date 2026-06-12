---
title: "Karmic Thinkpad X41 Tablet Stylus Problem"
date: 2009-11-11
forum: Hardware
---

### Post by beuvietnam on 2009-11-11
Dear all,
I'v just installed Karmic on my Thinkpad X41 Tablet. Everything working smoothly, except one thing: stylus.
The problem is: stylus is working but there are 2 bands with about one-inch-width (~ 20 mm) on the right and on the bottom of the screen that the stylus can not reach. The cursor dissapears when the stylus moving over on these areas (bands).
Please help.

---

### Post by Favux on 2009-11-11
Hi beuvietnam,

Welcome to Ubuntu Forums!

Hopefully it's just a question of calibrating your stylus with wacomcpl.  The problem is wacomcpl won't work unless:
```
xsetwacom list
```
in a terminal returns stylus and eraser.

To see what HAL is calling them enter:
```
xinput --list
```

There's a couple of ways to get around the problem.  See "Jaunty (9.04) & Karmic (9.10) Users" near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  See 3 and 3a.

---

### Post by beuvietnam on 2009-11-11
> **Favux said:**
> Hi beuvietnam,

Welcome to Ubuntu Forums!

Hopefully it's just a question of calibrating your stylus with wacomcpl.  The problem is wacomcpl won't work unless:
```
xsetwacom list
```in a terminal returns stylus and eraser.

To see what HAL is calling them enter:
```
xinput --list
```There's a couple of ways to get around the problem.  See "Jaunty (9.04) & Karmic (9.10) Users" near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  See 3 and 3a.

Thank you Favux,
I will try and report later.
Thanks again for your help.

---

### Post by beuvietnam on 2009-11-14
Dear all and Favux,

I followed instruction that Favux mentioned above.
1. I installed this 
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4-4.tar.bz2
```
following this Favux's instruction: [PHP]http://ubuntuforums.org/showpost.php?p=6546012&postcount=1[/PHP]
2. I made "wacom.fdi" file as described here: [PHP]http://ubuntuforums.org/showthread.php?t=1292227[/PHP]

After that I have:
1. xsetwacom list returned:
stylus           stylus    
eraser           eraser    
2. wacomcpl is working

seem everything have installed correctly,

BUT the stylus still can not reach the gray areas: the right and the bottom of the screen.

So, please help me if I was wrong somewhere?

---

### Post by beuvietnam on 2009-11-17
I have installed new beta package [linuxwacom-0.8.5-4.tar.bz2]("http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-4.tar.bz2")
but the problem is still there.
Please help me to check where is wrong.

---

### Post by Favux on 2009-11-17
Hi beuvietnam,

Looking at your screen shot this looks like a hardware problem.  I think the digitizer is failing.  With luck it may be just a matter of a loose connector from the screen/digitizer to the motherboard.  Or it may be a problem with the connections along the screen edges.

There are some sites describing repair I've seen when googling.  But not a lot of information that I recall.  Something about tape/connectors along screen edge??

---

### Post by beuvietnam on 2009-11-19
Thank you Favux,

You are absolutely right!!!
I have re-installed Windows XP and Wacom driver for Windows XP and the same problem appeared.
So we can say: Wacom serial tabletpc on Thinkpad X41 works great with Karmic without any additional install.

Anyway my son is very happy with Edubuntu and Tux Paint on the remain good working screen area. :)

I will make this topic [SOLVED]

Thanks all for your helps.

---

