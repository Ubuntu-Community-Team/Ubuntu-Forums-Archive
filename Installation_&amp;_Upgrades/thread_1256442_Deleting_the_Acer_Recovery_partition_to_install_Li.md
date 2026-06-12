---
title: "Deleting the Acer Recovery partition to install Linux?"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by gnuwtey on 2009-09-02
I recently (actually, just yesterday) got an Acer Aspire 8730G laptop, with Windows Vista preinstalled.

I want to repartition the hard disk so that I can multi-boot Vista, Fedora, and Kubuntu. (Vista will get 60 GB, Fedora and Kubuntu will get 16 GB each, and the other 228 GB will go to storing files and giving Linux some swap space.)

However, there are *two* recovery partitions on the computer - one at the beginning and one at the end. I've created recovery disk images for the partitions according to the eRecovery option given by Acer, but I don't know if they're enough.

Also, I need to back up the MBR, but I don't know how to do that.

I'll also be creating a system backup image so that I can delete all the partitions and put the Windows one back the way I had it before I moved the partitions around.

Does anybody see anything wrong with what I'm doing, or should I go for it...?

---

### Post by presence1960 on 2009-09-02
One of those recovery partitions will put the factory image back on your hard disk. most vendors give you the option of burning a set of bootable CDs/DVDs from that partition that you can use to restore the factory image. The other partition is probably a utility partition that services the sofware Acer put on with windows. But at any rate you really should refer to your documentation and see which one is which. You also should burn the bootable CDs/DVDs if given the option. Again refer to your Acer documentation. For good measure I would make an image of both of those partitions for safe keeping and store it on an external drive for safe keeping.

Then and only then would I delete or alter those partitions.

I would not remove the actual recovery partition that restores the factory image because you seem to have more than enough space to use. Take 10 or 15 GB away from that data partition and use that for Ubuntu. Just my opinion!

Instead of backing up MBR, you can go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn a Vista recovery console CD. you can use it to fix MBR as if you had a Vista install disk to use but you can't install Vista from it. if you ever need to fix the MBR so Vista bootloader is on it, use this disk.

> I'll also be creating a system backup image so that I can delete all the partitions and put the Windows one back the way I had it before I moved the partitions around.

That is what the recovery partition & bootable CDs/DVDs do. But it won't hurt to do it. You will have a lot of backup if you want to restore the factory image.

---

### Post by gnuwtey on 2009-09-02
> **presence1960 said:**
> One of those recovery partitions will put the factory image back on your hard disk. most vendors give you the option of burning a set of bootable CDs/DVDs from that partition that you can use to restore the factory image. The other partition is probably a utility partition that services the sofware Acer put on with windows. But at any rate you really should refer to your documentation and see which one is which. You also should burn the bootable CDs/DVDs if given the option. Again refer to your Acer documentation. For good measure I would make an image of both of those partitions for safe keeping and store it on an external drive for safe keeping.

Then and only then would I delete or alter those partitions.

I would not remove the actual recovery partition that restores the factory image because you seem to have more than enough space to use. Take 10 or 15 GB away from that data partition and use that for Ubuntu. Just my opinion!

Instead of backing up MBR, you can go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn a Vista recovery console CD. you can use it to fix MBR as if you had a Vista install disk to use but you can't install Vista from it. if you ever need to fix the MBR so Vista bootloader is on it, use this disk.



That is what the recovery partition & bootable CDs/DVDs do. But it won't hurt to do it. You will have a lot of backup if you want to restore the factory image.

 Thanks for your reply. For some reason, I didn't get much documentation with the laptop, but I looked online and the first one is the backup partition.  Also the problem isn't with space, it's with the fact that all four partitions have been used up. And I really don't want to install Ubuntu onto an extended partition...  I've already created the bootable CD's and DVD's and are testing them right now.  The DVD's do a goob job of restoring, but when I reboot, I get the error that "RCD.dat does not exist". What might that problem be...?  I haven't removed or done anything to any of the partitions, BTW.

---

### Post by presence1960 on 2009-09-02
> **gnuwtey said:**
> Thanks for your reply. For some reason, I didn't get much documentation with the laptop, but I looked online and the first one is the backup partition.  Also the problem isn't with space, it's with the fact that all four partitions have been used up. And I really don't want to install Ubuntu onto an extended partition...

Ubuntu and any linux distro run very well on logical partitions inside an extended partition unlike Windows. if I had to choose I would keep the recovery partition and make an image of the backup partition. But however you want to do it will work- **as long as you make backups or images of the partitions you remove.**

---

### Post by gnuwtey on 2009-09-02
> **presence1960 said:**
> Ubuntu and any linux distro run very well on logical partitions inside an extended partition unlike Windows. if I had to choose I would keep the recovery partition and make an image of the backup partition. But however you want to do it will work- **as long as you make backups or images of the partitions you remove.**

 Alright, thanks. That's what I've done.  But now, I'm currently trying to restore my system without removing the recovery partitions, just to test out the recovery disks, but it gives me that the partition's total size is 0.0 GB, which is a problem. 

Oh, actually... I deleted the DATA partition because it had nothing in it and I wanted to create an extended partition out of it. But it worked the first time, and that was *after* I deleted it.

Oh, wait, no, the Vista Recovery Center fixed it.

---

