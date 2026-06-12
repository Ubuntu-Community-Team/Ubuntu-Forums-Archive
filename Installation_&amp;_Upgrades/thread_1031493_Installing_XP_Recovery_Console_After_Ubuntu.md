---
title: "Installing XP Recovery Console After Ubuntu"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Tofystedeth on 2009-01-05
I recently had to wipe and restore my computer, so I took that opportunity to finally get around to installing Ubuntu on it.  So far it's great, but I have a question.  I have an XP install on there, but I forgot to put the recovery console on there before I did Ubuntu.  

Will doing it now screw up GRUB?  Do I even need to use it?  I assume most/all of the recovery console is needed for could be done from Linux.

---

### Post by lemming465 on 2009-01-06
> I forgot to put the recovery console on (XP)
If you have a bootable XP disk, you can run the recovery console from that, so in that case I wouldn't bother.  
> Will doing it now screw up GRUB?
I don't think installing the recovery console messes with the master boot record (MBR), so whatever dual-boot strategy you are currently using would probably survive.  If you boot via GRUB first and windows grabs back the MBR, you can boot an ubuntu live desktop, mount your root partition, and use *grub-install* to put it back.
> I assume most/all of the recovery console is needed for could be done from Linux.
You can do a lot of maintenance, particularly data recovery, from Linux, yes.  You can't run chkdsk for NTFS from Linux, or edit the Windows registry, or install windows software.

---

