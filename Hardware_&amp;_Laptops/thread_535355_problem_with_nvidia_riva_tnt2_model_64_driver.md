---
title: "problem with nvidia riva tnt2 model 64 driver"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by syms on 2007-08-26
hello,
when i install envy drivers, and restart x server then x server dont start and get error - nvidia driver not found. when in xorg i change nvidia to nv, then x server works, but with no drivers. i think problem is that in restricted drivers manager it shows your hardware dont need any restricted drivers. but when i start ubuntu from live cd and open restricted drivers manager then it shows nvidia accelerated graphics driver. what should i do? i need to reinstall ubuntu? my version 7.04 feisty fawn. thanks of all your help
p.s. sorry in english.

---

### Post by jimrz on 2007-08-26
> **syms said:**
> hello,
when i install envy drivers, and restart x server then x server dont start and get error - nvidia driver not found. when in xorg i change nvidia to nv, then x server works, but with no drivers. i think problem is that in restricted drivers manager it shows your hardware dont need any restricted drivers. but when i start ubuntu from live cd and open restricted drivers manager then it shows nvidia accelerated graphics driver. what should i do? i need to reinstall ubuntu? my version 7.04 feisty fawn. thanks of all your help
p.s. sorry in english.

make sure that envy installed and you are attempting to use the correct driver. your card needs the "nvidia-glx-[COLOR="Red"]legacy[/COLOR]

---

### Post by syms on 2007-08-26
yes, envy detects automaticaly my driver and it uses legacy driver.

---

### Post by syms on 2007-11-26
actually this is envy bug

---

