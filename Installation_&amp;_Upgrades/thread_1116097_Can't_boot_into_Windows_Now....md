---
title: "Can't boot into Windows Now..."
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by roystreet on 2009-04-04
Hi - I have a delima & maybe you can help me?  I was silly and deleted 2 partitions on my computer: swap & ext3.  I did that because I wanted to put a fresh install of ubuntu on it.  The other 2 partitions are windows partition. One a recovery partition & the other is the actual OS.  I wanted a dual boot system.  It used to work great while using grub. Well now that I reboot, grub gives me an error 22 & doesn't go to Vista. 

I've loaded the live the live version of ubuntu 8.1 & the Vista partition looks all nice & pretty and I can open & BACKUP my files just fine. When I try to install ubuntu it gives me an error when it's trying to partition and aborts.  I'm not totally sure what the problem is?? I'm quite sure that it has something to do with the boot loader which I have obviously messed up.

I would like to be able to boot windows again. I also want to have ubuntu again, but a fresh install - Which was my original intent anyway.

Any ideas?  It looks like I might just install Vista over again & then ubuntu after that so that it uses grub, but I would like to try to avoid it since I believe windows will work still if the bootloader worked.

Thanks,
~roystreet

---

### Post by ronparent on 2009-04-04
Your fuctioning grub was deleted along with your deletion of the ubuntu partiotion. Since the grub mbr portin of the bootloader depends on that to function, then grub as been broken. You have two alternative:

1) Just install ubuntu to your now unallocated space it formerly occupied. The grub bootloader will be restored in the process.

2) To just get windows to work for the time being until you install a fresh ubuntu, use the your windows install disk to restore your windows mbr. Be aware that the ubuntu install will ultimately overwrite the win mbr with a grub mbr at the time of an ubuntu install.

I recommenend 1) if you have the ubuntu distro at hand for an immediate install.

---

### Post by roystreet on 2009-04-04
ronparent - Thank you for your help. When I tried to install ubuntu in that space it would abort, so that wasn't an option. It would abort at the partitioning process

Unforutantely my HP came with a restore disk & not a regular windows disk.  After I backed up the windows files I wanted save most via ubuntu live I decided I would try different ways before reinstalling everything.

The HP restore disk didn't give me any type of option of restoring the mbr or anything like it. I didn't have a MS restore point & besides I don't think that would restore the mbr anyway.  There was an option that allowed me to do check disk. I thought why not? I tried it & it found errors, but in the process (It doesn't tell you this) it rebuilt the mbr. Once it did the checkdisk, I told it shut down. 

I restarted the machine & it booted windows just fine & dandy - Oh goodie!

Now the next "goodie" (I most excited about) was to install ubuntu. It had to manually create a swap & root because the guided process would abort on me...Don't know why?  Anyway, now I'm here typing while usuing linux!!  Yea! What a wonderful day...HeHe

*So anyone, checkdisk via your HP restore disk may rebuild the mbr.

Thanks for your help,
~roystreet

---

### Post by ronparent on 2009-04-04
Glad to hear everything is falling into place. There are many ways to get to the same place. You seem to have found one thru your own initive! Great!!

---

