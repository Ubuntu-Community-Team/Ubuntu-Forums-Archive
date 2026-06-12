---
title: "strange disk mounting problem"
date: 2008-08-17
forum: General Help
---

### Post by jhecker on 2008-08-17
I have an external disk from an otherwise destroyed notebook mounted in a USB case.  On that disk is an NTFS partition and some Linux partitions.  NTFS is the first partition on the drive.

I can mount the NTFS partition just fine; while I can see the other partitions with fdisk I cannot get them to mount.  I am not a newbie to Linux, but I am baffled - I figured if I could see the partitions, I could mount them.  They are ext3.  

Any pointers on troubleshooting from the experts here?

TIA -

jh

---

### Post by tamoneya on 2008-08-18
can you show us the output of ```
sudo fdisk -l
```That way we can tell you the correct commands.  Also it wouldnt hurt to tell us what commands you tried.  That way we can tell you why they failed and that way you can learn a little more from it.

---

