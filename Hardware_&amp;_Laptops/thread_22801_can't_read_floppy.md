---
title: "can't read floppy"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by lorap on 2005-03-29
this error i get once i try to mount floppy:

/dev/fd0: Invalid argument
mount: I could not determine the filesystem type, and none was specified

i understand it's possible to determine the fat needed in /etc/fstab,but i donno
which one :-)
probably there're additional solutions that would be welcome also :-)
thanks.
pavel

---

### Post by arctic on 2005-03-30
try with this option in /etc/fstab

/dev/fd0        /media/floppy0  **vfat**    rw,user,noauto  0       0

---

### Post by rykel on 2005-04-07
Hey artic,

I just bumped into the same problem with a floppy too... I thought it was my drive that was dirty (haven't used it for more than a year!!), but after cleaning, the filesystem error persisted...

Thanks to your instruction, I changed "auto" to "vfat" and it worked immediately. Thanks again!

btw, I simply wonder why the "auto" function could not detect vfat, which is the most commonly used floppy filesystem in the world possibly... oh well, I love Linux.    \\:D/

---

### Post by jhudson on 2005-04-07
I have the same problem and I did exactly the same thing and still doesn't work.
The reply says special device fd0 does not exist. What else could be wrong?

---

### Post by lorap on 2005-04-08
hi friends!
yup i know how to connect floppy manually in the terminal window,i've done it even in redhat 5 years ago.that wasn't the case.i was wondering why doesn't ubuntu recognize the floppy once i put it in.
but thank for the help anyway friends.
if you get any ideas let me know please.
pavel

---

### Post by nad on 2005-04-09
Not only did I change the type to ' vfat,ext2 ' in /etc/fstab, I also added vfat, autofs and floppy to my /etc/modules as they were not being listed by lsmod. I was having trouble unmounting without the -l switch even after modifying fstab. Now everything is working correctly.

Dan M

---

