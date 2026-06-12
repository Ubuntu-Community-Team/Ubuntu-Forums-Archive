---
title: "Resize Partition"
date: 2005-11-05
forum: General Help
---

### Post by kverde on 2005-11-05
Hi Ubugurus,

I recently installed Breezy as a dual boot to my Windows XP laptop...  Turns out I *can* use Linux and enjoy doing so.

Well, as you can see in the attached pic., I did not leave myself much room for the Ubuntu install.  I know I can use QTPARTED from KNOPPIX or other live CD.  But the catch, I guess, is that you cannot enlarge a partition by moving the beginning (only the end). 

So, I supposed I need to shrink my windows partition, move Linux to the newly freed space, then extend that linux partition.  At this point, everything should be cool except for the boot manager pointing to the correct Ubuntu Linux partition.  

Do I simply edit grub.conf?  If so, what do I put where?  

Thanks for the help!

---

### Post by az on 2005-11-05
If you do it the way you describe, the partition names should not be changed when you are finished.  

If you get stuck, yes, /boot/grub.conf and /etc/fstab

You can reinstall grub by chrooting into the filesystem and running 

grub-install /dev/hda

---

### Post by kverde on 2005-11-06
Cool, thanks for the tips.  I'll give it a try after I back everything up.

---

