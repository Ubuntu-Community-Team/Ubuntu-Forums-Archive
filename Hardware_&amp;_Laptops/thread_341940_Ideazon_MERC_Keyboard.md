---
title: "Ideazon MERC Keyboard"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by Meesh on 2007-01-19
Has anyone had any success getting the Ideazon MERC Keyboard to function fully?  I currently use the Ideazon ZBoard, and I have had zero difficulties with it - plug and play as it were.  But the MERC has been a different beast entirely.  
I know that Ideazon hasn't deigned to put out any Linux drivers for their MERC board, so I would love to know if someone has found a solution.

Thanks

---

### Post by Moordrik on 2007-03-13
I have been doing some reading regarding what it would take to get the Merc working completely.  It seems that xkb would be the best option, but it doesn't support anyting over 128 keys because of it's 8bit scan code limitation.  The merc, being USB uses 16 bit codes to define it's keys from what I am learning. I keep seeing referrences to a xkb patch that extends xkb to recognize these additional keys natively.....although the one and only link I have ever seen to it on dev.gentoo.org was in fact broken.  At this point I am dead in the water with this.  I know I could figure this out and get it completely working if:

1) xkb was capable of understanding the Merc's scan codes (from what I am reading)
2) the documentation of xkb wasn't so poor.
3) a guide was available explaining how one goes about generating custom maps for these keyboards, such as getting scan codes, generating the xkb files, etc.


I haven't played with xkb, don't know much about it, but I'm looking into it.  I really don't want to have to keep shifting back from XP to Ubuntu because of a keyboard.  I'm 99% where I want to be with Ubuntu/Wine, the only major sticking point is this keyboard.


Before someone says, "Just buy a new Keyboard" let me just say "No".  I'm willing to put the effort into making this happen if someone will point me to a guide(s) on what the process is, and what needs to be done.

---

### Post by Moordrik on 2007-03-16
Meesh take a look at this thread I started regarding the MERC, I almost have it working completely now, apart from the directional WASD and strafe keys not working correctly.  It's almost a full solution, and I am optomistic that it's just a matter of time until I have it completely working.


[http://www.ubuntuforums.org/showthread.php?t=385426&highlight=zboard]("http://www.ubuntuforums.org/showthread.php?t=385426&highlight=zboard")

---

