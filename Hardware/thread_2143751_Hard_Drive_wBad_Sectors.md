---
title: "Hard Drive w/Bad Sectors"
date: 2013-05-09
forum: Hardware
---

### Post by partloer on 2013-05-09
Is it likely to get bad sectors because of loss of power on a desktop computer?

---

### Post by Mark Phelps on 2013-05-10
Most likely -- no.  

What CAN happen is that the filesystem gets corrupted due to incomplete writes and/or directory updates.

If you want help, it would do better if you would describe the problem and its symptoms for us.

---

### Post by tgalati4 on 2013-05-10
Loose cables could cause problems, but more likely is old age.  How old is the disk drive?

---

### Post by partloer on 2013-05-11
This was on my Dad's desktop computer standard 1TB Seagate SATA.  The computer is less than three years old so it came as a surprise to me that it failed so soon.  I had daily backups to another computer so all the data was fine.  But I was trying to find out that cause of the problem in order to better prevent this from happening again.  I know that hard drives do fail from time to time (that is why I had a backup) but I have really only had problems with portable systems (laptop, portable hard drives, etc).  The problem became obvious when he could no longer log into windows 7 it would just freeze before the log in screen.  I attempted some of the repair method tools that come with windows 7 however none of them worked (I could not get chkdsk to run).  I later ran disk utility from the ubuntu live disk which showed the drive had bad sectors.

---

### Post by Mark Phelps on 2013-05-11
That is surprising that a Seagate drive failed that soon.  I used to swear by WD drives, but then, I had three fail me in a single year, and one was only a few months old.

So, drives can and do fail after a short period of use.

But simple power failures are unlikely to cause a drive to fail by themselves.

---

### Post by partloer on 2013-05-11
Thanks Mark.  That is kinda my thought just an anomaly but wasn't sure if there is more to it.

---

### Post by tgalati4 on 2013-05-11
If the computer was on 24/7 for 3 years, then I would suggest it is toast as consumer drives have the reliability just above that of a Christmas toy.  I would install* smartmontools* during a Live session and look at the SMART parameters.  There may be something else going on with the drive.

---

