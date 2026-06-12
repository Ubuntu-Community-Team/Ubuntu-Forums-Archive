---
title: "grub recognixing disk by uuid?"
date: 2008-11-21
forum: General Help
---

### Post by maestrobwh1 on 2008-11-21
I noticed in Intrepid, my grub menu.lst had

Title
**UUID="uuid of disk"**
kernel /bootpath/kernel uuid="uuid of disk" bootparameters
initrd /initrdpath

where **UUID="uuid of disk"** 

seems to replace 

root (hd1,0)

How far back will grub understand this.  I ask because with modern bios being able to boot from almost anything, sometimes I pop in my ipod, and forget to remove it before booting and then it is read as (hd1,0) rather than some disk I want to boot from that is usually (hd,1,0).  The uuid seems a better idea.

---

