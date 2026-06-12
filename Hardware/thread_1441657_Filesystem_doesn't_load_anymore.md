---
title: "Filesystem doesn't load anymore"
date: 2010-03-29
forum: Hardware
---

### Post by Kruptein on 2010-03-29
I was just surfing on the internet and making some changes to my webserver when my computer suddenly shutdown

When I rebooted it, the white-ubuntu sign (karmic), was shown way too long and then it started a filesystem check but wasn't even able to get to 1% o.O
I can only access a secure shell with my root account and I can still reach all my files trough this shell.

BUT how can I restore the file system?

---

### Post by Fafler on 2010-03-29
First, make sure the filesystem is mounted read-only do a ```
echo test > test
``` and it should complain about the filesystem being read only. If it doesn't, ```
mount -o remount,ro /
```

Then check the filesystem with ```
fsck /
``` and answer yes to fix any errors. Then you just need to reboot and anything should hopefully work again.

---

### Post by Kruptein on 2010-03-29
Well it's read-only.
Can I still do those commands?
 
EDIT: nevermind :p I misunderstood your answer I will try it as soon as poissible thanks

---

### Post by Kruptein on 2010-03-31
Well I did it and the white ubuntu icon disappeared  and a loading icon appeared but this stays (I left on my computer for a whole day and it just was there a whole day)  I'm able to login to my account via recovery mode but I don't know what I can do there to solve this...

---

### Post by Kruptein on 2010-03-31
Bump

---

