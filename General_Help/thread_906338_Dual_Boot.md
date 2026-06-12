---
title: "Dual Boot"
date: 2008-08-31
forum: General Help
---

### Post by karuzo on 2008-08-31
Hello all,
   I posted this in another forum, but got no responses hoping someone will see it here:

I have a laptop with one internal hard drive dual boot windows and ubuntu partitioned accordingly, where windows is on the main partition. Unfortunately I MUST use windows for about 2-3 programs where I need to utilize the graphic card in full (something as I understand virtualization won't provide at the moment).
Anyway, I am running out of hard drive space for both OS's.
Instead of upgrading to a bigger internal hard drive (really don't want to go through re-installation of ubuntu and re-configuration as I have it at the moment), I'd like to increase the partition for ubuntu, eliminate windows off the hard drive. Is it possible at this state to run windows xp off an external usb hard drive? From researching I found that windows 'requires' first partition?
I am going to try the essential windows application under virtual box, but unfortunately I don't even have room to install them there.
Virtual box related question (that possibly will determine if I can ditch windows all together). Anyone who owns a blackberry - is it possible to have virtual box (or even any commercial-grade virtualization software) to recognize usb and blackberry in particular?
Thanks,
Doron

---

### Post by WRDN on 2008-08-31
Boot from the Ubuntu LiveCD, or any liveCD that contains a partitioner, and you can use GParted to resize the partitions. Alternatively, if there are multiple files you rarely access but want to keep, you could compress them.

---

### Post by karuzo on 2008-08-31
> **WRDN said:**
> Boot from the Ubuntu LiveCD, or any liveCD that contains a partitioner, and you can use GParted to resize the partitions. Alternatively, if there are multiple files you rarely access but want to keep, you could compress them.

Thanks. If I repartition my windows partition won't have allot left that I can efficiently utilize. I'm really looking into installing windows on an external drive I have, but don't know if this is possible as I think windows requires first partition to run, as well as it will overwrite grub (?).
Thanks,
   Doron

---

### Post by MatthewPlanchard on 2008-08-31
You might consider setting up as follows:

approx. 10 gig root partition for Ubuntu
approx. 10 gig Windows o.s. partition
1 gig swap partition
Use the rest for a /home partition

Store all your documents, music, files, etc. on your home partition, and use a program like ExtIFS to access them from Windows.

---

### Post by karuzo on 2008-08-31
> **MatthewPlanchard said:**
> You might consider setting up as follows:

approx. 10 gig root partition for Ubuntu
approx. 10 gig Windows o.s. partition
1 gig swap partition
Use the rest for a /home partition

Store all your documents, music, files, etc. on your home partition, and use a program like ExtIFS to access them from Windows.

Thanks. That seems like what I might have to do eventually. However, I am still curious on installing windows on an external usb hard drive.

---

### Post by Sorivenul on 2008-08-31
MatthewPlanchard may have a point, but if you really want to try Windows on an external, maybe look at this site: [http://www.ngine.de/index.jsp?pageid=4176]("http://www.ngine.de/index.jsp?pageid=4176")

Good luck!

---

### Post by falcon61102 on 2008-08-31
You would probably be better off running Ubuntu off the External.  I do that every night at work since I can't install Ubuntu onto the work computers.  It works great.  Allows me to have my XP install on the computer with all the room I need there, plus I can have my Ubuntu install available.  Windows is going to give you a bit of trouble with being on an external for a few reasons besides just wanting to be the first partition.  With all the security features that windows has to attempt to keep people from ripping them off, it will not like being on a portable device.

---

### Post by karuzo on 2008-09-01
Thanks Guys. It appears as running windows on an external drive is not possible or at least not a good idea. I guess my next step is cleaning the hard drive from some files to get more space as well as backing up what I can. Most likely I'll install a second hard drive in my laptop which will probably be the best solution assuming I'll have then to reinstall windows AND ubuntu.
Doron

---

