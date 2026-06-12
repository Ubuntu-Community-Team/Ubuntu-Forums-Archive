---
title: "SMP Install"
date: 2005-11-11
forum: General Help
---

### Post by kurgan on 2005-11-11
I downloaded the .iso to install ubuntu.  How do I tell it that I have 2 processors?  I did it once and it only recognized 1, so I wiped it and am trying to find out where to select this.  Can I, or do I have to do something post install like install a different kernel?

---

### Post by Kyral on 2005-11-11
You'd have to install another kernel (post-install) which is easy

If you have a Pentium4 SMP then

```
sudo apt-get install linux-686-smp
```

If its an Athlon XP chip then

```
sudo apt-get install linux-k7-smp
```

and reboot

---

### Post by kurgan on 2005-11-11
Thanks much!  Worked like a charm!

---

### Post by Carzzzer on 2005-11-14
How about a good old dual P3-550 MHz?

sudo apt-get install linux-686-smp ?

---

### Post by Carzzzer on 2006-01-03
Would this kernel update not require a re-compilation of nearly everything?
Or is this just something that is glued to the existing kernel?

---

