---
title: "[SOLVED] How do I wipe a Hard drive (fill with zeros)"
date: 2008-10-15
forum: General Help
---

### Post by deltaromeo on 2008-10-15
Hello, I need to completely wipe a 320GB IDE HDD by filling it with zero's.  Does anyone know a way to do this that won't take all year?

Note: I don't want to wipe it by filling it with random data as further down the line I will be taking a full image of the drive which will then be compressed.  The free space will compress a lot better if it is all 0 than if it is random data.

Thanks!

---

### Post by geirha on 2008-10-15
```
sudo dd if=/dev/zero of=/dev/sdX
```
With /dev/sdX being the drive you want to fill with zeros. Make sure you choose the correct one ;)

---

### Post by adam_kimber on 2008-10-15
Have a look at the first post in [this thread]("http://ubuntuforums.org/showthread.php?t=943306"). I think that is what you are after. 

WARNING This will completely wipe all data from the drive in question. Make sure you have the right drive information before proceeding with this command.

---

### Post by Girya on 2008-10-15
> **deltaromeo said:**
> Hello, I need to completely wipe a 320GB IDE HDD by filling it with zero's.  Does anyone know a way to do this that won't take all year?

Note: I don't want to wipe it by filling it with random data as further down the line I will be taking a full image of the drive which will then be compressed.  The free space will compress a lot better if it is all 0 than if it is random data.

Thanks!

sudo shred -n1 -z </drive> 

will overwrite the drive with random data then finish with a write of zeros. K

---

### Post by jerome1232 on 2008-10-15
If you don't want to wait a year for dd to do it's thing you might want to change the command to something like this
```
dd if=/dev/zero of=/dev/sdXX bs=10M conv=notrunc
#or
dd if=/dev/random of=/dev/sdXX bs=10M conv=notrunc
```

---

### Post by Ganton on 2008-10-29
Take the solution of an expert at [http://www.feyrer.de/g4u/#shrinkimg](http://www.feyrer.de/g4u/#shrinkimg)  (he is the author of g4u)

---

