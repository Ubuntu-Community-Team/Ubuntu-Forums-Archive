---
title: "Suspend Error - Laptop Won't Wake Up After Suspend"
date: 2016-05-19
forum: Hardware
---

### Post by joelbitar1986 on 2016-05-19
Hello,

I've been having an issue with my Asus UX305 laptop since installing Ubuntu. Basically whenever I suspend/hibernate my laptop or if the screen is closed (which initiates a suspend), the computer won't wake up. The only thing I can do is restart at that point. I am including two pictures of the error message that Ubuntu provided at the next startup. Any input would be appreciated.

Thanks,


[ATTACH=CONFIG]269171[/ATTACH][ATTACH=CONFIG]269172[/ATTACH]

---

### Post by dblack49 on 2017-03-04
I had the same problem and spent ages (many days) trying this and that from every corner of the internet - some very complex - all to no avail.  And then, almost serendipidously, discovered that it was the Gparted app - it was locked to the Launcher bar / strip; I unlocked it (i.e. removed it from the Launcher) and that simple little measure fixed the problem. Now, WHY GPareted should cause the problem I can't say - perhaps some learned fellow / lassie could explain?  Regarding your problem - if you have GParted on the launcher remove it (by right-clicking and "Unlock from Launchbar").  If you don't have GParted then perhaps it is some other app that is locked to the Launcher?  Anyway, good luck and best wishes. DB

---

