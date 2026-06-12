---
title: "Migrate from bootable internal to external HD"
date: 2015-12-22
forum: Hardware
---

### Post by RBLevin on 2015-12-22
Hi,

I'd like to use an new 4T external USB3 or SATA HD to boot Ubuntu 15.10. Currently my ASUS laptop booths Ubuntu 15.10 from the 1T slow-as-mud internal HD. I'm looking for direction on the steps I need to take to migrate the internal HD in its entirety to the external HD and set the external HD as the boot drive.

I have a few additional questions about this:
- Can I use dd to do this?
- Once it's on an external device, can I use that device to boot Ubuntu on other PCs (if yes, do the drivers adapt dynamically if supported)?

Thank you.

Rich

---

### Post by sudodus on 2015-12-22
If you want to use the 4TB drive in a good way, you should have a GUID partition table, GPT, (and not an old style MSDOS partition table), and it is more difficult to clone a drive with GPT compared to a drive with MSDOS partition table. You cannot do it with dd and get it right at once, but it might be possible to fix it afterwards with some tools, for example ***gdisk*** in expert mode.

If the current system is a GPT system, you might be able to clone it with ***Clonezilla***, and after that fix it with for example gdisk in expert mode.

It might be easier to make a fresh install and maybe afterwards to copy the home directory from the old system, and to install the program packages again, (that you might have installed before instead of cloning them).

An alternative to cloning is to create the partition table and partitions, and then use ***rsync*** to copy the partition(s) with Ubuntu. It can be done according to the following link.

[Re: Best way to clone/copy a hard drive?](http://ubuntuforums.org/showthread.php?t=2306927&p=13409531#post13409531)

Finally you need to fix that the system will boot, which is different in UEFI mode and BIOS mode. You have to decide which mode you want to use, and one thing that makes a difference is if you are dual booting with Windows or some other operating systems. Are you running in UEFI mode to BIOS mode now?

-o-

Depending on the tips that you get here (not only from me), you should decide if you want to try cloning or porting the whole system or making a fresh install.

---

### Post by weatherman2 on 2015-12-22
Yes, you can use dd.  No, I don't recommend it - use Clonezilla instead.  You can make a bootable USB flash drive (you'll have to erase the whole flash drive in the process) or at worst make a bootable CD.

Yes, you can boot an external hard drive with Ubuntu on other computers.  I have done it many times.

I would expect an external drive to be not necessarily faster than the internal drive, however - it might even be slower.  Why not replace the internal drive with an SSD if you want more speed?  I prefer to use big external drives for storage or backup and use smaller, portable drives or USB flash drives for booting operating systems in a portable manner.

---

