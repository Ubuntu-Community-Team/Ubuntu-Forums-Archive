---
title: "Replacing hard drive"
date: 2010-09-19
forum: Hardware
---

### Post by RogerD on 2010-09-19
Hi

I'm planning to give my four-year old PC a heart transplant - new motherboard, new processor and new hard drive. As a first step I want to replace the current hard drive. I currently backup all my important files to an external hard drive (80G) and off-site, using deja dup and S3. One approach would be to simply replace my existing hard drive, install a fresh copy of Ubuntu, and then re-build my installation using my backed-up files. It would work, I think, but would take quite a while to get everything as it was before.

Is there some way I can copy my current hard disk image, of 32G, onto my external hard drive, install the new hard drive, and then use the Ubuntu installation CD to copy my old disk image onto my new hard drive, after which I would, hopefully, be able to re-start my PC with everything as it was before.

Regards

Roger D

---

### Post by sikander3786 on 2010-09-19
You can use many tools for that. I'll recommend remastersys and clonezilla.

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by cascade9 on 2010-09-19
If your replacing the hard drive, motherboard and CPU (and RAM as well would be a good idea, even if your current setup has DDR2 and your getting a new DDR2 board) get a new power supply..unless you've got a _very_ good power supply from 4 years ago.

Its not worth risking new parts on an old power supply.

---

### Post by RogerD on 2010-09-19
Thanks for the reply

I installed remastersys, but got the message:

The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again.

Back to square one it seems.

Roger D

---

### Post by RogerD on 2010-09-19
Thanks for the suggestion. I've recently upgraded to 2GByte of matched pair 800MHz DDR2, so I think the RAM situation is fine. The power supply is specific to my Antec NSK 3480 case, so if I keep the case, which seems fine, I'll have to keep the power supply. I wasn't aware that this could be a problem. Can you explain why you think it's an issue?

Roger D

---

### Post by sikander3786 on 2010-09-19
Try to clean up the archives, apt-get cache and any extra files you don't want to backup.

Remastersys has got a limit for the backup image. I think it is 4GB.

---

### Post by RogerD on 2010-09-19
4 GB is far too small for my purposes. It's beginning to look as though a fresh install, copying backed-up files, and installing non-standard applications is my best bet.

---

### Post by RogerD on 2010-09-19
Thanks to installing remastersys, I've now got a 23.9 GB folder cluttering up my home folder. I'm told I'm not the owner, so I can't cut it.

Any ideas?

---

### Post by sikander3786 on 2010-09-19
Did you try clonezilla. It is also a very capable software. No size limits I believe and it is can also be run off a live CD.

---

