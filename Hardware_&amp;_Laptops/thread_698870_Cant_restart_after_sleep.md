---
title: "Cant restart after sleep"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by fatmano on 2008-02-16
Help!!! I am running Kubuntu Gutsy and recently installed kpowermanager to allow my laptop to sleep when I closed the the lid. Last night it hung while trying to sleep. Now when I restart I cant get past boot up. The error that I see that stands out is :

RAMDISK: Couldn't find valid RAM disk image starting at 0.
VFS: Cannot open root device "801"m or unknown-block(8,1)

I am downloading a knoppix ISO now in hopes that I can remove the sleep image and just get it to boot. What I need I think is some directions to where the file might be and if there are any flags that I need to reset.

TIA


btw
I also posted this under general help too.

---

### Post by fatmano on 2008-02-16
No love over on the Gen. Help forum either.  Am I the first person that this has happened to?

I am running gutsy on an HP dv9500

---

### Post by pizpot on 2008-02-27
I heard from a KDE guy at a presentation that they hang out on ICQ helping people too. I turned sleep mode on my aspire with Fn+F5 and now it sleeps after reboot too :-( This happened to my an pavillion that I tried... to fix both I had to boot to xp and back to ubuntu.

---

### Post by fatmano on 2008-02-27
So I had to solve it a bit more unorthodox way.  I created a small partition with some left over disk space and installed gutsy on it, this wrote a new grub file and my old ( hung ) gutsy is listed.  So now I just boot to that and all is well with the world.  Not the best solution, but I needed to get back to work :(

---

