---
title: "Get windows back"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by rolyreefer on 2009-06-29
I have tried a couple of times to install Ubuntu a couple of times and can't get it to boot up.  I cannot use my computer except for by putting the install cd in.

I was running windows vista on a different disk before and was wondering if it is possible to get this back without reinstalling windows.  I was intending to run both for the time being and was wondering if it is possible, how to do this?

Thanks,

roly

---

### Post by lotster on 2009-06-30
I've heard a lot of complaints regarding the problems with Windows Vista dual-booting with Linux; apparently the two OS's boot managers have some issues with one another.

I recommend running a Vista repair installation from the Vista DVD; alternatively, follow the instructions at [http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html ]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html")or look at [this post]("http://ubuntuforums.org/showthread.php?t=475281").

---

### Post by rolyreefer on 2009-06-30
I have tried what it said but it didn't work.  It did say that the operation was successful, but it only gets to the run startup repair / run vista, black screen, but then reboots.  I have ruin startup repair from the disk (didn't work on the black screen), which  took over 2 1/2 hours and still didn't work.  I just tried the fixmbr bit again but still the same. 

Any ideas?

Thanks very much.

---

### Post by Mark Phelps on 2009-06-30
You may have to run startup repair several times.  It apparently only finds and fixes one problem at a time and then shuts down.  Three times should be sufficient.

---

### Post by sirhalos on 2009-06-30
Check to see if the Vista partition is the active partition from fdisk that might be the problem

---

### Post by rolyreefer on 2009-06-30
I have run startup repair 3 more time (quickly!) and still the same problem.  I have written down the failed bits as below:

2 Failed:

Boot manager failed to find os loader

repair action: file repair
result: failed error code: 0x3

repair action: boot config data store repair
result: failed error code: 0x490

Thanks again.

---

