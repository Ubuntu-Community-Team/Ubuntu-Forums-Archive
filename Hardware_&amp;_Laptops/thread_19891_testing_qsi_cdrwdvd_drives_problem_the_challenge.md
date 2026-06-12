---
title: "testing qsi cdrw/dvd drives problem: the challenge"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by burlap on 2005-03-14
It seems that cdrecord can't erase cdrw on QSI drives. This is the reason why, for example, nautilus-cd-burner doesn't work at all (for cdrw) and blanking doesn't work in gnomebaker, graveman and xcdroast. 

But it turned out that using "-immed" option for cdrecord fixes the problem. 

So, if there are any unhappy qsi drive users that want to test cdrw blanking ("at your own risk" as cdrecord man pages suggest): go for it and report the results.  ](*,) 

I have also filed a [relevant bug](http://bugzilla.ubuntu.com/show_bug.cgi?id=7382). 

```
cdrecord -immed -blank=minimal -dev=yourdev
```

---

