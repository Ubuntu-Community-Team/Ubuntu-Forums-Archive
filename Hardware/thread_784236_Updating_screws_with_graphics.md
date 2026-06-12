---
title: "Updating screws with graphics"
date: 2008-05-06
forum: Hardware
---

### Post by TUOggy on 2008-05-06
I don't know if this is a known problem, but if it is, I haven't been able to find anything about it.

I have recently installed 8.04 because it is the LTS.  I upgraded from Gutsy.  Before I installed Hardy, everything was working great, and at first, so was Hardy.  I manually installed all my graphics drivers, and made sure everything was working.  Then I updated.  I restarted after the update, and then my graphics driver stopped working (I got a warning message explaining that I was in safe graphics mode, and when I went to configure, my drivers weren't available).  I though it may have been something that I did, so I tried to fix it, and I couldn't figure it out, so I just decided to reinstall Hardy.  Same thing happened.  This happened about 5 times (I installed the drivers manually three times, once with envy, and once using Ubuntu's restricted drivers utility) and each time I got the same problem after installing drivers.

Finally, I just decided to turn off updates altogether, but that kind of defeats the whole purpose of me moving to an LTS in the first place.  

Is there some way that updates and graphics can work together?


I have an HP Pavilion dv6000 with a 256mb NVIDIA GeForce Go 7400, 2gb ram, 2.0 Intel duo core processor.

---

### Post by TUOggy on 2008-05-15
so nobody else is having this problem?

---

### Post by F34R1355 on 2008-05-15
I had a problem like this with a machine that had a Radeon 9250 PCI, and another machine that has a Radeon 9800. The 9250 refused to start in anything but safe mode. The 9800 lost most of its performance.

---

### Post by TUOggy on 2008-05-15
What did you do to fix it?  Or did you?

---

### Post by Sadprof on 2008-05-16
I too had a similar problem after up'ing from 7.10 to 8.04 (Geforce 8800GT). After a restart I found ubuntu in safe-mode with 800x600 as highest option.
Followed this post: [http://ubuntuforums.org/showthread.php?t=793078&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=793078&highlight=nvidia) with succes.
It basically says: install the latest 171.something driver from nvidia with their supplied script. Brought my graphics back to life. Even compiz worked beautifully. AWN needed a bit of tampering but this one [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive) helped a lot :)

gl!

---

