---
title: "(help) cant install grub after xp install"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by jareddlc on 2009-07-11
Hello ive recently install 9.04 and XP, however for some reason my machine was being pick (hp mini 1030) and it wouldnt install 9.04 after XP so i had to install 9.04 then XP( 8.10 would install perfectly) in doing so, XP replaces boot, now i cant grub back i tried these directions with no success. 

sudo grub
find /boot/grub/stage1   (no /boot folder is found)
root (hd?,?)
setup (hd0)
quit

So my 16gbSSD is as follows 
5gb    10gb
9.04   XP

so 1st partition or hd0,0 should be 9.04 and hd0,1 should be xp and where current /boot folder is?? i am unsure but partition editor has /boot flag under it.

so i was wondering how i could fix this to allow me to get grub and see both OS possibly install grub before getting into livecd.i dont have a clue on what to do. please ask for any clarification if i didnt do a good type up.  Thx in advance

---

### Post by merlinus on 2009-07-12
You might try this:

```
sudo grub 
root (hd0,0)
setup (hd0)
quit
```

---

### Post by jareddlc on 2009-07-12
> **merlinus said:**
> You might try this:

```
sudo grub 
root (hd0,0)
setup (hd0)
quit
```

Err sorry for any misunderstanding i copied and pasted the directions from a website i did do hd0,0 not ?

---

### Post by arindambhattacharya on 2009-07-12
try this...use live CD open terminal and...

sudo grub 
find /boot/stage2
.....(hdX,Y)
root (hdX,Y)
setup (hdX)
quit

---

### Post by merlinus on 2009-07-12
If none of this works, try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by jareddlc on 2009-07-12
no luck. going to reinstall. hopefully it will let me

---

