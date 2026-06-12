---
title: "Spinning down and external hard drive"
date: 2008-09-15
forum: Hardware
---

### Post by elewton on 2008-09-15
SOLUTION:
hdparm -Y /dev/sdX

Is there a command that allows me to spin down an external hard drive?  When I unmount the drive and lift it I can still feel a gyroscopic effect.
When I disconnect it, it make a horrible whiny noise.

I use it for storage for my laptop, but I think I'm shortening its life time.

Much appreciated,
Thanks.

---

### Post by sdennie on 2008-09-15
You could try using hdparm with either the "-y" or "-Y" option on the disk.  Using hdparm can be dangerous but, those options aren't labeled as being particularly dangerous.  Have a look at the man page ("man hdparm") and see if one of those options suits your needs.

---

### Post by elewton on 2008-09-15
Thank you very much.  I had seen hdparm mentioned, but when I read the Wikipedia page, it looked like it could only configure parameters.  I wasn't aware that it could also do things.

Thanks again!

---

