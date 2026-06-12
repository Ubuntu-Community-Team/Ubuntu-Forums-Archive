---
title: "Thinkpad R50"
date: 2010-04-20
forum: Hardware
---

### Post by PhilMize on 2010-04-20
Hey guys', I'm trying to revitalize this older Thinkpad R50 and so far its been fairly easy going with 9.10. Though I can not get the sound to work. I ran **lspci** and can see my audio hardware but am unsure of the next step to take. Any suggestions? I've also tried turning up all the settings under alsamixer. 

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

---

### Post by PhilMize on 2010-04-20
bump:popcorn:

---

### Post by Shmoozen on 2010-04-20
Kind of unrelated, but I'm having trouble booting 9.10 netbook remix on my thinkpad R50. It installed fine, but when i boot it says "error: no such device" I installed it off a flashdrive if you're wondering.

Do you know what the problem is? O.o thanks!

---

### Post by PhilMize on 2010-04-22
> **Shmoozen said:**
> Kind of unrelated, but I'm having trouble booting 9.10 netbook remix on my thinkpad R50. It installed fine, but when i boot it says "error: no such device" I installed it off a flashdrive if you're wondering.

Do you know what the problem is? O.o thanks!

Your probably having trouble because UNR is not ment to run that sort of laptop. UNR only runs on Intel Atom architecture and some other "mobile" architectures. The Intel Centrino processors in the R50 are not support. Course, you could always make it supported, this is linux after all. But just install 9.10 desktop edition and you'll be set.

Refer to the hardware requirements in this [link]("http://www.canonical.com/projects/ubuntu/unr").

---

