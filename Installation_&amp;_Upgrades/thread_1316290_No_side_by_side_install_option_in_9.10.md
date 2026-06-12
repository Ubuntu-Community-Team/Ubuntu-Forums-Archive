---
title: "No side by side install option in 9.10?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by edin9 on 2009-11-05
What gives?

---

### Post by werecatomega on 2009-11-05
well, i,m not sure what you mean but i'm guessing you mean a dual-boot, right? also, explain your predicament please, it makes it much easier for people to answer and understand what you need to do

---

### Post by edin9 on 2009-11-05
This. [IMG]http://i35.tinypic.com/11t50z8.png[/IMG]

---

### Post by Bob63 on 2009-11-05
I'm just guessing here, but it looks as if the entire space/partition on the drive is devoted to Vista - there is no place for 9.10 to install to. The usual suggestion I see is to run defrag in Vista once or twice then shrink the Vista partition to make space for Ubuntu.

Alternatively, you could spend some $$ and buy another drive and set it up the way you want, which is what I did. In my setup, I installed XP first, then Vista, then Ubuntu, each with its own partition on a 500GB SATA drive. My system boots into grub, which gives me the option of going to Ubuntu or running the Vista loader, if I choose the Vista loader it comes up and lets me choose between Vista or XP.

If you can't get enough "shrinkage", back up your Vista data and repartition the drive. Someone else may have a better idea.

Good Luck

---

### Post by edin9 on 2009-11-05
> **Bob63 said:**
> I'm just guessing here, but it looks as if the entire space/partition on the drive is devoted to Vista - there is no place for 9.10 to install to. The usual suggestion I see is to run defrag in Vista once or twice then shrink the Vista partition to make space for Ubuntu.

Alternatively, you could spend some $$ and buy another drive and set it up the way you want, which is what I did. In my setup, I installed XP first, then Vista, then Ubuntu, each with its own partition on a 500GB SATA drive. My system boots into grub, which gives me the option of going to Ubuntu or running the Vista loader, if I choose the Vista loader it comes up and lets me choose between Vista or XP.

If you can't get enough &quot;shrinkage&quot;, back up your Vista data and repartition the drive. Someone else may have a better idea.

Good Luck

Yeah it's f*cking Vista that's the problem, not Ubuntu. Defragged makes no difference. Shrinkage gives me 50MB, and GParted just refuses to do anything. Thanks anyway.

---

### Post by SunnyRabbiera on 2009-11-05
> **edin9 said:**
> Yeah it's f*cking Vista that's the problem, not Ubuntu. Defragged makes no difference. Shrinkage gives me 50MB, and GParted just refuses to do anything. Thanks anyway.

Even with compressing file systems Vista is very bloated.

---

### Post by QIII on 2009-11-05
You used Vista's native partition manager and it still only gave you 50MB after a couple of defags?

---

### Post by edin9 on 2009-11-05
> **QIII said:**
> You used Vista's native partition manager and it still only gave you 50MB after a couple of defags?

Yeah.

---

### Post by QIII on 2009-11-06
There is a Windows utility, I think it is called "filesize", that can tell you the sizes of all folders/files listed by size -- ascending or descending -- and where they are.

Don't know if it is free...  Probably not in the Windows world.

You might be able to find that and do some analysis.

Do you have a lot of large files, images for instance, in a file somewhere?

Do you have SQL Server (Developer or Express) on the machine?

---

