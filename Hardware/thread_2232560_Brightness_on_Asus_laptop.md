---
title: "Brightness on Asus laptop"
date: 2014-07-02
forum: Hardware
---

### Post by ckrles on 2014-07-02
Hi, I have an Asus Laptop A53S  (k53sc). I can control the brightness through the menus and Fn + F5 and F6, but there's a problem. Once I adjust the brightness it is not saved and once the computer is rebooted it sets to maximum again.

I have tried different changes in the grub files, but still no luck. I also installed xbacklight but I can't find it. Is there any way to permanently set the brightness to a specific value?

Hardware: intel i7, 4gb ram, Nvidia Geforece Gt 520MX. I don't know if it has to do with the fact that I haven't installed Nvidia drivers. I did installed Bumblebee.

I'm using Ubuntu 12.04 Lts.

Thank you very much.

---

### Post by lucianloonstra on 2014-07-03
Dear Ckrles, have you tried this: [http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart) ?

---

### Post by ckrles on 2014-07-07
> **lucianloonstra said:**
> Dear Ckrles, have you tried this: [http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart) ?


It worked. I had to add the value 1200 to get the desired brightness.

Thank you.

---

