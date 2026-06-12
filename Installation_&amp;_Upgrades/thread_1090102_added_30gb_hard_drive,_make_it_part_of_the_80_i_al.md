---
title: "added 30gb hard drive, make it part of the 80 i already have?"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by sansa dude on 2009-03-07
i just added a 30gb hard drive to my system. it is formated NTFS and i want to add it to the 80 so they both come up as one drive. is this possible? if so how can i do it?

---

### Post by sansa dude on 2009-03-08
any ideas? i will also add i switched the format to ext3 and if it is possible i do not want to have to reinstall ubuntu if it can be avoided

---

### Post by darco on 2009-03-08
I could only think it being setup as a RAID but not sure...you would have to google to see if that option works...Why do you want to set up as 1 drive? You could make the 30 gig drive your /root and /swap drive and the other hdd as your /home.

darco

---

### Post by sansa dude on 2009-03-08
> **darco said:**
> I could only think it being setup as a RAID but not sure...you would have to google to see if that option works...Why do you want to set up as 1 drive? You could make the 30 gig drive your /root and /swap drive and the other hdd as your /home.

darco

ok you know what, that would be better
do i just boot onto a live CD and just copy the files over? or is it a little more complicated than that?

---

### Post by taurus on 2009-03-08
It depends what you want to copy over and where you want to mount that second drive?

---

### Post by sansa dude on 2009-03-08
my 30gb drive is internal same with the 80gb so there is no problem there. would i just copy all the other files over but the home file? and would i have to go some where and tell ubuntu that the home file is in a diffrent place like you do with windows xp?

---

### Post by taurus on 2009-03-08
If you want to move your /home over to the second harddrive, you have to boot your machine with Ubuntu LiveCD.  Then, look at this guide especially about **Using the new partition**.

[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

---

### Post by sansa dude on 2009-03-08
ok so i do this if i want to keep the home folder on the 80gb and put every thing else on the 30gb?

---

### Post by darco on 2009-03-08
the 30 gig drive could be setup like:

/root 10-12 gigs
/swap (depends on your memory size) 256mb-2 gigs

then the rest as more storage...no need to waste it. 

darco

---

