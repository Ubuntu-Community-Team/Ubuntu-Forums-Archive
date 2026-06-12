---
title: "Worth  £37 ??"
date: 2008-09-20
forum: General Help
---

### Post by Thyssenkrupp on 2008-09-20
Seeings as theres no way of me installing XP, Is a 60Gb HDD with XP on it worth £37??

Its XP Home.

If i did use this, on my Dual Core 2ghz, 2Gb RAM using oncoard Nvidia 7050 graphics, would i be able to play spore ??

Thanks,

Jak

---

### Post by timothius on 2008-09-20
> **Thyssenkrupp said:**
> Seeings as theres no way of me installing XP, Is a 60Gb HDD with XP on it worth £37??

Its XP Home.

If i did use this, on my Dual Core 2ghz, 2Gb RAM using oncoard Nvidia 7050 graphics, would i be able to play spore ??

Thanks,

Jak

If the original machine that installed XP on the harddrive is different from yours then there is a high chance that it won't boot.

---

### Post by mb_webguy on 2008-09-20
Spore should be playable under Wine, assuming you are using the most recent version of Wine from the Wine HQ website, and have applied the patches as described in the Spore entry on the Wine AppDB site...

---

### Post by Thyssenkrupp on 2008-09-20
> **timothius said:**
> If the original machine that installed XP on the harddrive is different from yours then there is a high chance that it won't boot.


Why not?

Is there no way i can make it work?

---

### Post by Thyssenkrupp on 2008-09-20
> **mb_webguy said:**
> Spore should be playable under Wine, assuming you are using the most recent version of Wine from the Wine HQ website, and have applied the patches as described in the Spore entry on the Wine AppDB site...


I dont know how to apply patches =[

theres no guide that explains it in enough detail =[

---

### Post by Chokkan on 2008-09-20
> **Thyssenkrupp said:**
> Why not?

Is there no way i can make it work?
I think it's because when XP was originally installed, it would have kept important details like what the motherboard, RAM, monitor were. If those aren'T the same, then it might not boot.

---

### Post by mb_webguy on 2008-09-20
> **Thyssenkrupp said:**
> I dont know how to apply patches =[

theres no guide that explains it in enough detail =[

It tells you how on the [Wine AppDB Spore page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652").
> Patch and compile your copy of wine with [this]("http://bugs.winehq.org/attachment.cgi?id=15883") patch. If you're using git, then don't do this: git already has patches for the bugs in that patch. Otherwise, just use "patch -p1 < foo.patch" as normal.
Download the patch, then open the terminal, change to the directory where you downloaded the patch, then type that command (replacing "foo.patch" with the actual filename of the patch).

And make sure you have installed the most recent version of Wine from the Wine HQ database first.

---

