---
title: "[SOLVED] Resizing root partition"
date: 2008-09-28
forum: General Help
---

### Post by kooldino on 2008-09-28
I need to resize my root partition.  I had another partition on the same physical disk that I removed, and I'd like to grow my "/" partition.

I obviously can't do that while it's mounted.

I tried to boot off a GParted CD (along with some other boot discs) but they ran into an error that wouldn't allow it to fully load.

Is there an easy way to do this?

---

### Post by CorvisRex on 2008-09-28
If the gparted boot disc don't work for some reason, and you want to use gparted, just boot from the Ubuntu LiveCD,  once booted, just "apt-get install gparted" there is no reason you can't install an app from the repo.  Course, it wont be there after you reboot, but you can temporarily install apps while using the liveCD, and it will be there for the rest of the session.

---

### Post by binbash on 2008-09-28
You have to do it gparted live cd.you cant work on gparted if the drive is mounted

---

### Post by kooldino on 2008-09-28
> **CorvisRex said:**
> If the gparted boot disc don't work for some reason, and you want to use gparted, just boot from the Ubuntu LiveCD,  once booted, just "apt-get install gparted" there is no reason you can't install an app from the repo.  Course, it wont be there after you reboot, but you can temporarily install apps while using the liveCD, and it will be there for the rest of the session.

That's basically what I just did.  However, to install it, it had to write to my swap disk, which is the 2nd partition on that same drive.  So I unmounted that, did my resizes and moves, and viola...I can't believe it actually worked!

---

