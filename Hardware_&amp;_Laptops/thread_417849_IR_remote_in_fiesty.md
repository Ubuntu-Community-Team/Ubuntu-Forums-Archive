---
title: "IR remote in fiesty?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Spartan.II.117 on 2007-04-21
hi, i'm trying to set up a remote to control the media on my laptop (I use rythem box as it has support for wma's) i found lirc but have no idea how to use it and recompiling the kernel noes not sound like fun, can anyone help here?
the remote i'd like to use is a sony rmt-502, but i can find a universal one that i can program if that would be easier

Thanks, 
Spartan

---

### Post by Spartan.II.117 on 2007-04-22
i have since followed the instructions in [https://help.ubuntu.com/community/Install_Lirc_Feisty#head-661b91158a667cd25342be5b8b85c16ecc8491b3](https://help.ubuntu.com/community/Install_Lirc_Feisty#head-661b91158a667cd25342be5b8b85c16ecc8491b3) to the best of my ability, but i havejust about no idea what i'm doing, i'm using in internal irda port on my dell c610 laptop with the port set as com 1 and irq 4, can anyone help with this?

---

### Post by Spartan.II.117 on 2007-04-23
bump?

---

### Post by stacktracer on 2007-04-24
I can't help (yet), but I wanted to say that I'm in the same boat. I'll post here if I have any success.

---

### Post by stacktracer on 2007-04-24
Well, here's a small step in the right direction:

[http://ubuntuforums.org/showpost.php?p=867154]("http://ubuntuforums.org/showpost.php?p=867154")

**irrecord** doesn't seem to pick up any button presses at all, but **mode2** (mentioned in the linked-to post) spits out lots of numbers!


The first time I ran **mode2**, I got nothing ... but I think I was using lirc_serial. I unloaded lirc_serial, loaded lirc_sir, and then **mode2** succeeded in spitting out numbers.

---

