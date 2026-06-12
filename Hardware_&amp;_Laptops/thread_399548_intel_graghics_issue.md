---
title: "intel graghics issue"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by storky on 2007-04-02
i have a HP dv2000 laptop with a intel Mobile 945GM/PM/GMS/940GML graphics driver, wich seems to run very smoothly with ubuntu but i am running into one constant error when using wine.

i am attempting to run WOW but it happens with other programs as well. everytime i try to run it i get a error:

libGL warning: 3D driver claims to not support visual 0x5b

by searching this site i have noticed that other people have had simular problems with simular graghics cards. What i have not seen is a how to for an intel driver update. I cant find one from intel's website either.

when replying keep in mind that i am a ubuntu and linux newb.

i do not mind if i have to install a 3rd party graghics driver or something to that extent, i just want this problem solved.:KS

---

### Post by storky on 2007-04-02
just to clarify i am running 6.10 ubuntu

---

### Post by jordanmthomas on 2007-04-02
I don't think it's too big of a problem.  Correct me if I'm wrong, but a warning is not bad, while an error is.  I don't have the exact same card, but I do use the i810 drivers as Im sure you do.  

As far as I know, there is only one set of 3d-accelerated drivers for your card, so you're basically stuck with what you have.  Luckily, the warning is innoculous and won't stop you from doing anything.  You just have to see it pop up any time you run a 3d app (or winecfg for some reason).  

When you are trying to run WoW, does it still play?  If not, it's probably not this warning that is stopping you.

**edit** I don't get the error any more when I run winecfg or anything else for that matter.  So, apparently they have either a) fixed it or b) I got lucky.  I'm using Arch Linux by the way, but I still used to get the same errors that have now disappeared.  I guess there is hope for your problem after all.  I am using the i810 drivers version 1.7.4-2 from Arch

---

### Post by storky on 2007-04-02
no it does not play. i just assumed that this was the reason. now i am completely lost.

---

### Post by jordanmthomas on 2007-04-02
Well, are any other errors given when it crashes?

---

### Post by storky on 2007-04-02
well there is a bunch of writing but my computer freezes before i could ever copy and paste it

---

