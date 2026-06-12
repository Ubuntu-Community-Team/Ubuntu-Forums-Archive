---
title: "Problem with hard drive."
date: 2010-12-13
forum: Hardware
---

### Post by guilleme on 2010-12-13
Hello everyone, well, I've got a problem with my mom's computer. The computer is an old compaq presario 2100 (yep, from those days compaq was actually a competitive business, and not part of hp). Now, the problem is that it won't boot up. I tried booting windows on the "secure" mode, but it won't do. I tried then with a live dvd having Ubu. 10.10 on it, and wouldn't boot either, so, I went to the bios, and tried to run a hard drive self-test, but, not having even started, it gave me an error, "#1- 07fail", I'm exasperated.
I belive the thing is refusing to boot ubuntu because the processor is an old amd athlon M.
A little detail, the thing ubuntu says when the boot process halts, is about the process 270 calling for a user-id, and getting an un-known one, 0. Literally: "(process:270): Glib-WARNING**: getpwuid_r(): failed due to unknown user id (0)". then it halts.
Thanks very much in advance, appreciate it. 
Hope somebody can help.

---

### Post by dabl on 2010-12-13
I would proceed on the assumption that the hdd is dead (or dying).

If BIOS allows it to boot from a CD, then you should be able to boot a *buntu Live CD, assuming you got a good md5sum and burned it slow.  It may or may not support booting from DVD ...

---

### Post by coffeecat on 2010-12-14
> **guilleme said:**
> I belive the thing is refusing to boot ubuntu because the processor is an old amd athlon M.
A little detail, the thing ubuntu says when the boot process halts, is about the process 270 calling for a user-id, and getting an un-known one, 0. Literally: "(process:270): Glib-WARNING**: getpwuid_r(): failed due to unknown user id (0)". then it halts.

If you mean booting Ubuntu from the DVD, then I doubt whether that's because the CPU is old. Those are the sort of errors you get when the original downloaded ISO is corrupted, the disc is bad, or the optical drive is not reading it properly. If you've checked the md5sum and done a slow burn as dabi suggests, that might suggest your optical drive is faulty/failing. Using a DVD instead of a CD for the Ubuntu ISO is not a problem, so long as your optical drive can read DVDs. Try burning another Ubuntu disc.

---

### Post by guilleme on 2010-12-14
Well, I believe the processor has something to do with the error because it isn't even similar at the hardware point to intells (it's not an x86), and it's not an amd64 either, it has the old 32 bit amd arquitecture with software intell implementation, and the disc I'm using was compiled for x86 processors, but I'm quite shure the cd works because I have used it with other computers recently, and it has worked, so, it's not the disc.

---

### Post by coffeecat on 2010-12-14
[AMD Athlons]("http://en.wikipedia.org/wiki/Athlon") are x86 compatible processors and the x86 32-bit version of Ubuntu is 100% compatible with them. If the CD is OK then the optical drive is not.

---

### Post by guilleme on 2011-01-06
well tried with a cd, and it worked!

---

