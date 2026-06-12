---
title: "Formatting large disks question"
date: 2008-10-08
forum: General Help
---

### Post by Jay Rutherford on 2008-10-08
I'm running 8.04 and all is well. I got a 640 GB USB external hard drive at Costco and gparted it as Ext3 to use for backup or maybe a server for other PCs in the home. After rounding down the nominal "640 GB", I have about 590 GB of space.

When I examine the volume, I see nearly 5 GB of space used with nothing on the hard drive except the lost+found file. 

Is this a normal amount of overhead on a drive of this size? Is there any way (or would I want to) remove the lost+found file?

Thanks all.

Jay

---

### Post by jerome1232 on 2008-10-08
Normally there's (5%?) space reserved for... well I don't remember why it's reserved just that it is. Perhaps someone else will know the intricacies of it.

edit: I believe it was  so that if the disk fill up, 5% is reservered for root so that you can still boot up. It also prevents file fragmentation on a full disk.

---

### Post by Jay Rutherford on 2008-10-08
Thanks Jerome. Your edited remarks make sense. I'll just go with it as I have a long way to go before those reserved bytes will come into play.

Jay

---

