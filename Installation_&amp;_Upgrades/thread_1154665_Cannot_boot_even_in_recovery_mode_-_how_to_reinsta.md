---
title: "Cannot boot even in recovery mode - how to reinstall without formatting?"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2009-05-10
I accidentally deleted some critical system files on one of my ubuntu systems to the point where it won't even give me a login prompt in Recovery mode.  It's running 9.04 and I have a working 9.04 live cd.

Is there any way to reinstall the base system without having to back everything up and reformat?

Note I don't have a separate /home partition but I don't want to go through the trouble of backing everything up and reformatting unless it's **absolutely necessary.**

I read some threads here and it says to try doing:

 apt-get install ubuntu-desktop

Unfortunately, I cannot boot up this system without using a live CD.

---

### Post by zvacet on 2009-05-10
You can make separate home following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") or [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.After you do that reinstall Ubuntu on top of root partition and **don´t format home**.

---

### Post by bjm442 on 2009-05-10
I have the same problem.  I was going for 8.10 to 9.04, and nothing comes up.  I also don't want to reformat, since my e-mail is on that pc.  not sure what to do next.

---

### Post by mosaic2s on 2009-05-10
To save your e-mail data, check out profile folder.
Try USB pen drive for booting the system and transferring e-mail data on that.

---

