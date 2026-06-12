---
title: "Can you write to an external ntfs drive with a live ubuntu disc?"
date: 2009-01-21
forum: Hardware
---

### Post by firsttry on 2009-01-21
I'm trying to help a friend remotely (meaning I can't do complicated things) who's got a broken version of Windows - she wants to backup her important data before re-installing an OS.

I suggested running the Ubuntu live cd and copying the data she wants to backup to an external hard disk - however the external hard disk she has is NTFS...

She can't place her laptop's hard disk in the external hard disk case as it's got a frame glued to it (go figure) so she can't stick the pins into it.

Does the Ubuntu live CD come with NTFS-3G installed? Is it possible just to run an 'aptitude install ntfs-3g' to install the program within the live CD environment?

Any help would be appreciated!

---

### Post by 2hot6ft2 on 2009-01-21
> **firsttry said:**
> 
Does the Ubuntu live CD come with NTFS-3G installed?
Yes, it shouldn't be any problem to do what you're trying to do. Just have her wait until the live desktop is up and running before plugging the drive in so it will automatically mount it and open nautilus.

---

### Post by firsttry on 2009-01-21
Thanks for the quick answer, I'll let you know how it goes.

---

### Post by 2hot6ft2 on 2009-01-21
You're welcome and good luck. You shouldn't have any problems.

---

### Post by firsttry on 2009-01-21
Another thing - will Ubuntu also automount the hard disk that is *in* her computer (also NTFS)? The one she needs to copy data from? Where will it mount it to?

---

### Post by 2hot6ft2 on 2009-01-21
> **firsttry said:**
> Another thing - will Ubuntu also automount the hard disk that is *in* her computer (also NTFS)? The one she needs to copy data from? Where will it mount it to?
No it wont auto mount it, but all she has to do is go to Places>(the windows drive) to mount it so she can move things. The first time you click on an unmounted drive it mounts it the second time you click on it you're going into it's file system where you can browse to what you want.

I think the 8.10 livecd has one click enabled so it would only take 1 click. Forgot I set mine to double click to open things.

---

### Post by firsttry on 2009-01-22
Worked beautifully! :)

Thanks!

Don't seem to have a medal icon or Thread Tools->mark as solved though :(

---

