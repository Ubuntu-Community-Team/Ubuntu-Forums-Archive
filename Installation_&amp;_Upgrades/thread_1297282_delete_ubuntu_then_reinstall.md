---
title: "delete ubuntu then reinstall"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by rvt20s on 2009-10-21
I have ubuntu installed alongside vista on my latop with grub. If I delete the ubuntu partition will it get rid of the grub menu and restore my laptop back to its original state when I just had vista?
Has anyone tried this and had no problems?

the reason I ask is I wish to shrink my windows vista partition and reinstall ubuntu in the unallocated space. I like ubuntu alot so I need more room... for upgrades and so fourth.

---

### Post by dhavalbbhatt on 2009-10-21
> **rvt20s said:**
> I have ubuntu installed alongside vista on my latop with grub. If I delete the ubuntu partition will it get rid of the grub menu and restore my laptop back to its original state when I just had vista?
Has anyone tried this and had no problems?

To answer your first question - my understanding is that you will not be able to get rid of grub - it will stay there. However, there are ways to remove grub and restore it to the original setting of booting directly into Windows (you will find plenty of posts in here on how to do that)

> **rvt20s said:**
> the reason I ask is I wish to shrink my windows vista partition and reinstall ubuntu in the unallocated space. I like ubuntu alot so I need more room... for upgrades and so fourth.
For the second part - why do you want to re-install? If all you want to do is increase the partition size of Ubuntu, then use GParted from LiveCD. Secondly - if you are really going to re-install, why not just leave grub there until you re-install?

---

### Post by presence1960 on 2009-10-21
> Originally Posted by rvt20s  
I have ubuntu installed alongside vista on my latop with grub. If I delete the ubuntu partition will it get rid of the grub menu and restore my laptop back to its original state when I just had vista?
Has anyone tried this and had no problems?
To answer your first question - my understanding is that you will not be able to get rid of grub - it will stay there. However, there are ways to remove grub and restore it to the original setting of booting directly into Windows (you will find plenty of posts in here on how to do that)

See [here]("http://ubuntuforums.org/showthread.php?t=1014708") (follow instructions for Vista)

If you have a recovery partition/DVD and don't have access to Recovery Console in Vista you can download an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it to CD and boot from it to follow instructions above

This will overwrite GRUB on MBR and replace it with Vista bootloader.


> Quote:
Originally Posted by rvt20s 
the reason I ask is I wish to shrink my windows vista partition and reinstall ubuntu in the unallocated space. I like ubuntu alot so I need more room... for upgrades and so fourth.
For the second part - why do you want to re-install? If all you want to do is increase the partition size of Ubuntu, then use GParted from LiveCD. Secondly - if you are really going to re-install, why not just leave grub there until you re-install?

+1.

Only thing there is don't use gparted to resize Vista's partition. use Vista's disk management utility to shrink Vista's partition to create free space. Then use gparted to add that free space to Ubuntu's partition.

The reason you don't want to resize Vista with gparted or any other outside partitioning utility is there is an as yet unresolved bug (see [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482")) which renders Vista unbootable if vista is resized with anything other than Vista's disk management utility. Although some people report success and Herman has reported he found a workaround, I would still err on the side of caution and shrink Vista with it's own disk management utility. Better safe than sorry.

---

### Post by rvt20s on 2009-10-22
Thanks for all the replys. The only reason I suggested I reinstall ubuntu was because someone told me it would be very hard to increase a ext3 partition.
I will start by shrinking Vista with it's own disk management utility and then take it from there.

---

