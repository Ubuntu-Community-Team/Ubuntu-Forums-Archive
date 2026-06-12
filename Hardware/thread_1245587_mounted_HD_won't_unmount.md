---
title: "mounted HD won't unmount"
date: 2009-08-20
forum: Hardware
---

### Post by vedek on 2009-08-20
hi guys,

Quick Question.

i have a external HD it mounted fine automatically. but it wont unmount. i go in to terminal and type

```
 umount /dev/sdb 
```

Can i just pull out the external or will that mess the system up.

by the way i checked my mtab and its not there.

---

### Post by vedek on 2009-08-20
I really got to stop doing this.

i type up the request for help and then i fix the problem myself. 

perhaps i should think about my problem more rather than saying help me.

by the way
i did

```
 sudo umount /dev/sdb1
```


i figured it out by relooking my mtab and fstab and found that it didn't load /dev/sdb but it had mount /dev/sdb1

---

