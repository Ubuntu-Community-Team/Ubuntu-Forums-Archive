---
title: "Can't read DVD without CD"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by bioman on 2006-06-26
hi all,

I have a DVD rewriter Plextor PX-716A, and while i put a DVD in it, it's detected like a  blank DVD.

I can read them only if I insert a CD before, why ?

---

### Post by jvl on 2006-06-26
how old is the drive? Could this be dust?

---

### Post by bioman on 2006-06-26
1 year old and no, thats not the dust.
I can read data DVD-ROM under XP without to put CD-ROM in it.

---

### Post by bioman on 2006-06-28
Any ideas ?

---

### Post by jer2eydevil88 on 2006-06-28
Have you searched for a firmware update on that drive? Could be the firmware is just not talking with linux correctly and a simple firmware update will solve that.

To tell what version of firmware is in the drive now just look it up with the nero drive tool.  You can then see if an update is available.

---

### Post by bioman on 2006-06-28
hello,

I just upgraded the firmware like you suggested, but the problem it's still here.

---

### Post by bioman on 2006-06-28
When i insert a dvd, dmesg report it :

"cdrom: This disc doesn't have any tracks I recognize!"

But it can read all dvd after i put a CD in it

---

### Post by ccc1 on 2006-06-28
[QUOTE=bioman]hi all,

I have a DVD rewriter Plextor PX-716A, and while i put a DVD in it, it's detected like a  blank DVD.

I can read them only if I insert a CD before, why ?[/QUOTE]

i have exactly the same problem with a Plextor 755A! it works fine under
xp but under ubuntu and SuSE i have to insert a cd before i can read a dvd.

manual mounting (i.e. mount /dev/hdc /mnt) works fine.

would be nice to see that fixed, it's annoying.

---

### Post by ccc1 on 2006-07-01
noone here with a 755A or 716A plextordrive who has or hasn't got this bug?

---

