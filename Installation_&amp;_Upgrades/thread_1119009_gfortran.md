---
title: "gfortran"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by myquidproquo on 2009-04-07
Hi!

I wanted to install gfortran but I get 

gfortran-4.3:
  Depends: gcc-4.3-base (=4.3.2-1ubuntu11) but 4.3.2-1ubuntu12 is to be installed
  Depends: gcc-4.3 (=4.3.2-1ubuntu11) but 4.3.2-1ubuntu12 is to be installed

Is there anyway that I can force the install or downgrade the other package? 

Thanks.

---

### Post by lisati on 2009-04-07
One thing to check is if you have build-essential installed:
```
sudo apt-get build-essential
```

---

### Post by myquidproquo on 2009-04-07
I have the 4.3.2-1ubuntu12...The problem is that it requires 4.3.2-1ubuntu11...And that is not on the repositories so I can't force it...

---

