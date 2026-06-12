---
title: "[SOLVED] Cannot delete shortcut."
date: 2008-09-01
forum: General Help
---

### Post by winbutu on 2008-09-01
Hey, i just have a super quick question that somenone will be able to awnser in their sleep.

I installed cod4 on my vista partition, but for some reason i got a shortcut to it on my ubuntu partition?

My first question is why?
My second is, why cant i delete the shortcut off of my desktop?

thanks in advance 

-winbutu

---

### Post by modmadmike on 2008-09-01
have you tried <shift>+<delete> or going into a terminal and doing a cd /"username"/Desktop then a sudo rm "filename"

---

### Post by knattlhuber on 2008-09-01
> **winbutu said:**
> Hey, i just have a super quick question that somenone will be able to awnser in their sleep.

I installed cod4 on my vista partition, but for some reason i got a shortcut to it on my ubuntu partition?

My first question is why?
My second is, why cant i delete the shortcut off of my desktop?

thanks in advance 

-winbutu

I have no idea why you would have that shortcut on your desktop.
Did you try deleting it via the terminal using

```
sudo rm /path/to/shortcut
```

---

### Post by winbutu on 2008-09-01
thanks, fixed!

---

### Post by modmadmike on 2008-09-01
Oh, and as for why are you sharing your /home directory with windows as your My Documents or User folder?

---

### Post by modmadmike on 2008-09-01
> **knattlhuber said:**
> I have no idea why you would have that shortcut on your desktop.
Did you try deleting it via the terminal using

```
sudo rm /path/to/shortcut
```

hey you stole my idea and modified it lol

---

### Post by winbutu on 2008-09-01
Just found out is was actually just the disk showing up on my desktop..


epic fail.

-.-

---

### Post by knattlhuber on 2008-09-01
> **winbutu said:**
> Just found out is was actually just the disk showing up on my desktop..


epic fail.

-.-

So you mean you just wiped out your Vista partition using 'rm'? :)

---

### Post by winbutu on 2008-09-01
lol, naww, the cod4 cd was in the drive, that was the desktop icon.

I will wipe out vista in a second...when i can play cod4 on ubuntu without WINE!

:(

---

### Post by modmadmike on 2008-09-01
How about running it in virtualbox, thats not using WINE lol. PS. wine works great on my desktop, I play WoW and HL2 in it all the time, as for COD4 i don't own a copy yet :(.

---

### Post by winbutu on 2008-09-01
Well i checked out WINE for cod4 and apparently evreything works except multuplayer, which is what i only play so....
Plus i dont care that much, my system auto boots into ubuntu.

---

