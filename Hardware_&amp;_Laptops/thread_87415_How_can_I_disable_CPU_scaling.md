---
title: "How can I disable CPU scaling?"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by Airspawn on 2005-11-08
My bios doesnt let me disable my cpu scaling. I'm using the 'CPU Frequency Monitor' and I've noticed something strange. Whenever my CPU frequency jumps, my laptop has a fart bubble for a second. It's becoming really annoying. I cant seem to find any GUI program in Ubuntu to disable the scaling. It's a pentium m @ 1.5 if that makes any difference.

Thanks, any newbie friendly advice would be appreciated.

---

### Post by 23meg on 2005-11-08
```
sudo killall powernowd
``` should help.

---

### Post by Airspawn on 2005-11-08
Wow, that was easy. Any way of making this permanent at startup? Thanks.

---

### Post by 23meg on 2005-11-08
Sure, check [this thread]("http://www.ubuntuforums.org/showthread.php?t=21370") out.

---

