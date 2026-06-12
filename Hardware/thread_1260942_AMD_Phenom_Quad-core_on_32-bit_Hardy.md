---
title: "AMD Phenom Quad-core on 32-bit Hardy"
date: 2009-09-08
forum: Hardware
---

### Post by mister_p_1998 on 2009-09-08
Thinking of upgrading my aging P4-3 GHZ to an AMD Phenom Quad core. I'd rather not go for a re-install, Im thinking of building the hardware and plugging my terabyte hard disk into the new box (32 bit Hardy i386) Ive done this with a dual-core at work with no problems, can I do this with the quad core? or would I need an AMD version of Ubuntu?
Steve

---

### Post by arcull on 2009-09-08
If it is just the cpu what you want to replace, as far as I know, you don't need to reinstall anything, however with new cpu you will probably need to replace mobo, this will result in different driver requirements, and you will must probably have to reinstall ubuntu. There is one more thing you might wan't to consider: you will have a quad 64 bit cpu and will put on a 32 bit system, isn't that a bit a waste? You know what you need, but since 64 bit linux is pretty mature now, you could pull out of your cpu much more with 64 bit kernel.

---

### Post by realzippy on 2009-09-08
...just plug in the cpu,it will work.Nevertheless 64 bit ubuntu has grown up by now......

---

### Post by mister_p_1998 on 2009-09-08
> **realzippy said:**
> ...just plug in the cpu,it will work.Nevertheless 64 bit ubuntu has grown up by now......

Ive heard a lot of horror stories about flash etc, and my install has TONS of files I dont want to fiddle about with, I only upgraded to Hardy from Dapper in June, and that was a task and a half!
Steve

---

### Post by Grenage on 2009-09-08
Phenom II Quad on AMD64 Ubuntu here, on several machines.  Works wonderfully (for me).

---

### Post by mister_p_1998 on 2009-09-08
> **Grenage said:**
> Phenom II Quad on AMD64 Ubuntu here, on several machines.  Works wonderfully (for me).

Hmm good, but I want to plug in a pre-installed i386 hardy into the quad Phenom.
Steve

---

### Post by Grenage on 2009-09-08
It 'should' work, you'll just be taking your chances.

---

### Post by jasonditz on 2009-09-08
There's no reason it should be any worse than running 32-bit Windows on a Phenom, which people do all the time. These chips are 64-bit but they're designed with the understanding that a lot of people were going to toss 32-bit OSes on them. 

Still, 64-bit Ubuntu is tight, you really should consider doing the upgrade at some point.

---

### Post by sideaway on 2009-09-08
Unfortunately I think you may run into issues galore. Going from a p4, 945? to a AMD platform 780? 770? 790? Without a reinstall, the different chipsets may prove troublesome. The CPU will be the least of your troubles, you can't just plonk an AM3 CPU in a p4 socket :P. Also performance won't be as optimal. I would suggest making a partition for you home drive, backing it up, and when doing a reinstall just mount the partition as your home dir. settings saved, modules updated! Good as gold :)

---

### Post by mister_p_1998 on 2009-09-09
When I say an AMD Cpu I mean a full pc minus hard disk, I realise a quad core AMD wont fit into a p4 mobo!

Steve

---

