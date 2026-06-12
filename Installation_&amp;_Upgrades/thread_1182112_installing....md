---
title: "installing..."
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Mueez on 2009-06-08
hey guys im installing xubuntu using "wubi" on my pc... it downloaded the iso file but now its stuck on "creating virtual disk"

what should i do??

---

### Post by N1c0_ds on 2009-06-08
> **Mueez said:**
> hey guys im installing xubuntu using "wubi" on my pc... it downloaded the iso file but now its stuck on "creating virtual disk"

what should i do??

Honestly, the best way would be to use a Live CD. I found the same bug on Google but no solutions.

---

### Post by presence1960 on 2009-06-08
> **N1c0_ds said:**
> Honestly, the best way would be to use a Live CD. I found the same bug on Google but no solutions.

+1

I just installed using wubi from Live CD and worked with no problem. I had to see what wubi is like since I never used it nor installed it. Am going to try it out to better my knowledge. So far I cant notice any difference, the only thing that is a concern is that windows fragmentation may affect performance. Other than that concern I can see no difference from my install to a partition. When the experiment is done I will uninstall wubi.

---

### Post by Andreas dB on 2009-06-17
My installation stucks also at 'creating the virtual disk', as wel with using Wubi as installing whith the live cd. I'm using Windows Xp sp3 with AMD Athlon 3000+ on an Acer machine.

---

### Post by Bucky Ball on 2009-06-17
> **presence1960 said:**
> the only thing that is a concern is that windows fragmentation may affect performance. 

Not really possible as Windows has no idea what an EXT3 partition is, therefore can't see it without some coaxing, and you will find you couldn't de-frag it if you wanted to (from Windows). There is generally little need to de-frag in Linux; different way of keeping track of files.

I would advise anyone to boot from the LIVE CD, and if you can't boot from that, your hardware is probably incompatible and will need to tweak some software or replace.

---

### Post by presence1960 on 2009-06-17
> **Bucky Ball said:**
> Not really possible as Windows has no idea what an EXT3 partition is, therefore can't see it without some coaxing, and you will find you couldn't de-frag it if you wanted to (from Windows). There is generally little need to de-frag in Linux; different way of keeping track of files.

not true according to the community documentation. Scroll down to the sentence after #11. [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Not referring to defragging ext3, but to performance due to windows fragmentation. The wubi is on the windows file system after all.

---

### Post by Bucky Ball on 2009-06-18
Got you, sorry. Yea, I imagine that could be a problem for Wubi install, sure. :)

---

