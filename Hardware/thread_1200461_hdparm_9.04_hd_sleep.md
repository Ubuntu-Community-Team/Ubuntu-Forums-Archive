---
title: "hdparm 9.04 hd sleep"
date: 2009-06-30
forum: Hardware
---

### Post by Simoo on 2009-06-30
My second IDE drive will not sleep, after a certain amount of time it just starts clicking repeatedly as if it is trying to sleep but being woken immediately. If I run 'hdparm -y(Y) /dev/sda' it also sleep/wakes immediately.

I have done some googleing on this problem and it seems others have had similar problems with 9.04. However, I haven't found a definite fix other than a suggestion to compile a newer version of hdparm from source?! 

I am a little concerned as this cant be good for the drive. Can anyone help?

---

### Post by Simoo on 2009-06-30
It turns out (thankfully) that the clicking was to do with the drive not being seated correctly in it's bay I think.

However, I am still unable to sleep the drive. Anyone know why?

---

### Post by Tomtefar on 2009-07-06
Maybe the os writes logs or accesses the drive every now and then, forcing the drive to wake up?

---

