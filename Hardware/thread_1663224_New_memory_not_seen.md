---
title: "New memory not seen"
date: 2011-01-09
forum: Hardware
---

### Post by ontwowheels on 2011-01-09
10.10 32bit generic.  Just added memory to a new laptop, 8GB total.  Memory is seen on my Win7 install but my 10.10 still shows only 2.4 in the system monitor.  Is that a limitation of the 32 bit version?

Thanks

---

### Post by Frogs Hair on 2011-01-09
Yes , the 32 bit version will not detect all your memory.

---

### Post by ontwowheels on 2011-01-09
Thanks.  And 64 bit is only for AMD CPU's correct?

---

### Post by paulisdead on 2011-01-09
No, if you've got an Intel core2 or later CPU, it will definitely support it.  The Intel CPUs run the 64bit extensions just fine.  If the CPU was made in the last couple years, it should have it.  Some of the late gen P4s supported it as well.  If it's a Celeron, you'll have to check the specific model you have to see if it supports it.

---

### Post by IcarusR on 2011-01-09
I believe you need the PAE kernel, which will enable you to see all your ram. 
The server 32 bit kernel supports PAE (Physical Address Extension).
Or as  paulisdead says use 64 bit kernel.

This post has info on 32 bit Ubuntu with 4GB+ of memory

[http://ubuntuforums.org/showpost.php?p=5359004&postcount=1]("http://ubuntuforums.org/showpost.php?p=5359004&postcount=1")

---

### Post by cascade9 on 2011-01-10
Just in case of any confusion- you can install the 323bit PAE kernel easy enough, but if you want to go to 64bit you will have to reinstall (which I would, PAE is still limited to 3/4GB of RAM maximum per process)

---

