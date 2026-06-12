---
title: "GRUB/XP Problems"
date: 2008-11-03
forum: General Help
---

### Post by benign on 2008-11-03
I had Ubuntu 8.10 and Vista loading through GRUB completely fine - no delays upon booting or anything. I decided to get rid of Vista and deleted all traces of it from it's partition. After that, I rebooted and installed XP to the NTFS partition that Vista was on. After rebooting, nothing happened... I was getting a disk read error. I loaded up the Ubuntu live CD and put GRUB back on the MBR by:

> 
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit


Once I rebooted, it took (now takes) about 15 seconds for the GRUB menu to come up, and it will load Ubuntu fine after that, but it still can't load XP. It just gives me a disk read error.

Any ideas?

---

### Post by TeXtonyx on 2008-11-03
Does the grub menu list XP as an option?
Make sure menu.lst correctly identifies the XP boot partition.
Later you may need to look at fstab for automatic mounting.

---

### Post by benign on 2008-11-03
> **TeXtonyx said:**
> Does the grub menu list XP as an option?
Make sure menu.lst correctly identifies the XP boot partition.
Later you may need to look at fstab for automatic mounting.

It was never automatically updated by the XP install, but the partition still appears to be correct according to various sources. This is what is in my menu.lst file - I just changed the name from Vista to XP.

> 
title Windows XP
root (hd0,0)
chainloader +1
savedefault
makeactive


As far as looking at fstab, how could that even matter in this case since it has to do with once linux is loaded and not before?

---

### Post by TeXtonyx on 2008-11-04
TeX wrote: Later you may need to look at fstab for automatic mounting.
-----------------------

benign asked: As far as looking at fstab, how could that even 
matter in this case since it has to do with once linux is loaded 
and not before? 
---------------------------

TeX: By "Later" I meant that after you had fixed the booting problem,
you might have an additional problem to fix. Below is my fstab
entry for sda1 (hd0,1). I'm not sure it would still be correct if
I repeated your process on my system, which is why I said "may".

/dev/sda1 /media/WindowsPro ntfs-3g defaults,locale=en_US.UTF-8 0 0
---------------

This is what is in my menu.lst file - I just changed the name from Vista to XP.

Quote:
title Windows XP
root (hd0,0)
chainloader +1
savedefault
makeactive
---------------------

Since something didn't work right, did you check your assumptions
by running  sudo fdisk -l ? Is the NTFS partition where you expect?

Did you run grub again?
sudo grub
grub>find /etc/boot/stage1
grub>root (hdX,Y) [using the information that "find" reports]
grub>setup (hd0)
grub>quit
--------------------------

Check to see if there is any duplication in menu.lst

benign wrote: "It was never automatically updated by the XP install,..."

I'm not sure what "it" is referring to. XP will overwrite the Ubuntu MBR.
Did XP boot? Then grub needs to be reinstalled so that once again the MBR
is controlled by Ubuntu which was covered above in the grub> commands. XP
doesn't act on the menu.lst file, so that is why the "it" is in doubt.
What should have been automatically updated by the XP install that wasn't?

---

