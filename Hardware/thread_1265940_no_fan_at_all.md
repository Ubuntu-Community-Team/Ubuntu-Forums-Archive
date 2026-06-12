---
title: "no fan at all"
date: 2009-09-14
forum: Hardware
---

### Post by yevelez on 2009-09-14
Hello. I have just installed ubuntu 9.04 in my toshiba laptop U505-S2930 and i can see that fan is not cooling at all. I mean, it is off!!!!

This is a very, very bad thing for the health of my computer. What do i have to do? Thanks a lot!

---

### Post by earthpigg on 2009-09-14
in theory, Ubuntu will regulate how much or little the fan is doing and it will regulate it well according to the needs of the CPU.

let's see how well that theory applies here.

first, boot from a LiveCD. how is the fan now?

if it isn't working on a 9.04 LiveCD, try an 8.04 one just for kicks. how is the fan there?

next, what does lm-sensors tell you?

to install it:

```
sudo apt-get install lm-sensors
```

to set it up, run this and say yes to everything:

```
sudo sensors-detect
```

you may need to restart your computer at this point for the kernel modules to be loaded and take effect. 

finally, please post the output of:

```
sensors
```


if your CPU is hanging around 50C or less, that is fine for a laptop.

if it is up at 75C and the fan is still not running and the two LiveCDs above both didn't get it going, then we have a problem --- the first thing i would check at this point is the physical fan itself. a long hair may have somehow gotten sucked in there and wrapped itself around the fan and have it jammed, for example.

---

### Post by pricorp on 2009-09-28
I am planning to purchase this computer and run Ubuntu on it.
Have you solve the fan problem ?

---

### Post by k33bz on 2010-03-30
[http://michaelminn.com/linux/toshiba-u505/]("http://michaelminn.com/linux/toshiba-u505/")

---

### Post by finito on 2010-04-29
[http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan&page=2](http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan&page=2)
got the fan to work

---

### Post by Kaneda187 on 2010-04-29
mark thread as solved if your done with this.
cheers

---

