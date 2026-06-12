---
title: "Can't find second hard driive."
date: 2008-11-27
forum: General Help
---

### Post by phreon on 2008-11-27
Hi Folks,

Searched the forums for an answer but no luck. 

I have Ubuntu 8,04 I just installed as dual boot Ubuntu and Win 98 on an old AMD Duron box with a 40Gb disk. Ran great.

I then added a second 160Gb disk from an old Win XP box. Both Ubuntu and Win 98 don't see it. BIOS lists it as a Primary Slave drive but the OS doesn't see it. In Ubuntu, when I go to the Places/Computer menu it shows my Ubuntu partition and my Windows partition and a SCSI drive that I can't mount. If I look at its properties it shows as "Unknown Type".

Any ideas what I have missed?

Thanks
P

---

### Post by Peter09 on 2008-11-27
Is the drive formatted. If not use gparted 


System->Admin->Partition Editor

to setup a partition. Make sure you select the right drive.

---

### Post by phreon on 2008-11-28
Hi,
Thanks for the quick reply. The drive was partitioned before I installed it but I ran gparted again and made one large partition. This is working now for some reason.

Thanks for the help.
P

---

