---
title: "Shutdown hangs up"
date: 2008-07-29
forum: Hardware
---

### Post by neonl on 2008-07-29
Hello all,

i'm having this issue randomly but basically what happens is that sometimes when i shutdown my Acer laptop, the screen goes black (after usplash), but it fans don't stop and the "power on light" doesn't go off. Sometimes this can happen without shutting down, just leaving it there without moving the mouse. As i said before, this doesn't *always* happen, it's random.

Cheers.

---

### Post by Potatoj316 on 2008-07-29
if you were to put acpi=force at the end of your menu.lst entry for whichever kernel you use it might make it not happen, but there might be some unwanted side effects.

---

### Post by neonl on 2008-07-29
Right... So this is unavoidable in Hardy, without having other side effects?

Thanks anyway :)

---

### Post by Potatoj316 on 2008-07-29
I dont know if anything will happen, it works fine for me.  Well one of my computers (an older one) needed it, the other works fine.  Post the output of ```
cat /boot/grub/menu.lst
``` and I can try to help.  

There is a reason they dont put acpi=force in by default, I just dont know what it is.  It might be because there is no reason to, or it might be because it creates problems.  But anyting it does can be fixed.

---

### Post by neonl on 2008-07-29
I can't post it now (it's on my mother's laptop, i use Gentoo in my box) but i'll check it out later. I think i understand the problem now that you mention it...

Thank you ;)

---

