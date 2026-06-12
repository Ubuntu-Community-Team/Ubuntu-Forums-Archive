---
title: "Problem with my hard drive"
date: 2008-08-04
forum: Hardware
---

### Post by spyderxombie on 2008-08-04
ok i have a 40 gig HD that my ubuntu is on...i just added a new 120 gig hard drive and formatted it using the ext3 format...when i go into places it shows the hard drive but it wont let me copy anything onto it, says i dont have permission...any ideas what to do?

---

### Post by logos34 on 2008-08-04
Here you go:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(-->bottom)

---

### Post by loboc on 2008-08-04
> **spyderxombie said:**
> ok i have a 40 gig HD that my ubuntu is on...i just added a new 120 gig hard drive and formatted it using the ext3 format...when i go into places it shows the hard drive but it wont let me copy anything onto it, says i dont have permission...any ideas what to do?

are you a memeber of the disk group

```
 man adduser
sudo adduser name disk
```

---

### Post by spyderxombie on 2008-08-04
i tried both of those...followed the steps closely...still no dice.  I just cant seem to put anything on the drive even tho it reads it.

---

### Post by cdtech on 2008-08-04
The drive is "root". You can create a directory withing the drive to copy to which will become user ownership.

---

