---
title: "LCD brightness."
date: 2008-09-09
forum: Hardware
---

### Post by wtfitsRICK on 2008-09-09
I've looked around, and this seems to be a common problem, but nothing solves it for me.  When I first installed, the screen was just as bright as it should have been.  Now my function keys won't work.  The toolbar brightness adjuster thing won't work, either.  I just want to be able to see my screen.

Compaq Presario C700

---

### Post by JMorg on 2008-09-09
Are you dual booting? because i'm curious how the brightness looks in your secondary operating system. It could be an inverter board (main board in the lcd) issue which is not software related. But if the LCD brightness is fine within your secondary OS then it's definitely a software based issue.

---

### Post by wtfitsRICK on 2008-09-11
> **JMorg said:**
> Are you dual booting? because i'm curious how the brightness looks in your secondary operating system. It could be an inverter board (main board in the lcd) issue which is not software related. But if the LCD brightness is fine within your secondary OS then it's definitely a software based issue.

Yeah, I'm dual booting with Vista.  When I'm using Windows, the brightness is just fine; it can be adjusted with the function keys.  So I'm not sure what's wrong.

---

### Post by ice2921 on 2008-09-12
same issue here Toshiba Satellite M45-S265

---

### Post by wtfitsRICK on 2008-09-12
> **ice2921 said:**
> same issue here Toshiba Satellite M45-S265

Did yours have proper brightness when you first used it, too?  I find that to be particularly strange.

---

### Post by ice2921 on 2008-09-12
Yeah but the strange thing is that the function keys used to work as well.There has to be a fix.

---

### Post by wtfitsRICK on 2008-09-14
I never tried the function keys, but here's the weird part for me: I used to have a partition of Hardy (even used the same disc) and the brightness issue never occurred.  Function keys worked then.

GUH.  It makes me sad.

---

### Post by meijer.o on 2008-09-14
Dear user:

Try this:

Add to /etc/modprobe.d/blacklist the module video

command: sudo gedit /etc/modprobe.d/blacklist

Add to  this file : blacklist video

save file and restart computer

---

### Post by wtfitsRICK on 2008-09-16
> **meijer.o said:**
> Dear user:

Try this:

Add to /etc/modprobe.d/blacklist the module video

command: sudo gedit /etc/modprobe.d/blacklist

Add to  this file : blacklist video

save file and restart computer

I'm not really sure what that means.
I'm fairly linux-stupid, so I don't really know what you want me to do.

::EDIT::
I just started up in Ubuntu, and the brightness is just fine.  I can't adjust it at all, but it's fully bright.  o.O

---

### Post by avinash_destiny on 2008-09-17
Even i am facing with same problem . 
compaq presario 3425au

---

