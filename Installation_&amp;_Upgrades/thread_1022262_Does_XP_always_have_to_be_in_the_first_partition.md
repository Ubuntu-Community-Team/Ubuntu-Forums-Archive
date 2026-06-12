---
title: "Does XP always have to be in the first partition?"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2008-12-26
As I recall, XP has to be the very frst partition in a multi-boot system.

If true, then I probably should just get a new big HDD , install my XP, then install a new ubuntu. Maybe I should just do that anyway, for backup reasons.

In fact, IIRC, XP not only has to be the first partition, it must also be the first system installed on the HDD.

Is that true?

---

### Post by logos34 on 2008-12-26
> **bliffle said:**
> As I recall, XP has to be the very frst partition in a multi-boot system.

...

In fact, IIRC, XP not only has to be the first partition, it must also be the first system installed on the HDD.

urban legend...

The only requirement is it be installed on a PRIMARY partition (there are exceptions).  And in the case of multidisk systems, the target drive must be set as the boot drive in the Bios, otherwise Windows will refuse to install.  

If you install Windows after linux, it will overwrite the bootloader.  But you can easily restore Grub from the live cd (see link my signature).

---

### Post by cariboo on 2008-12-26
The Windows boot files have to be on the first partition, otherwise Windows doesn't care where it is installed.

Jim

---

### Post by caljohnsmith on 2008-12-26
> **logos34 said:**
> urban legend...

The only requirement is it be installed on a PRIMARY partition (there are exceptions).  And in the case of multidisk systems, the target drive must be set as the boot drive in the Bios, otherwise Windows will refuse to install.  

If you install Windows after linux, it will overwrite the bootloader.  But you can easily restore Grub from the live cd (see link my signature).
+1. I agree, Windows wants a primary NTFS/FAT partition on the master drive to put its boot files. In my experience helping in the forums, that also means you can install Windows to a slave drive or even a logical partition, as long as Windows has a primary NTFS/FAT partition on the master drive where it can put its boot files. Afterwards it is possible to move the boot files back to the Windows partition (and it doesn't matter whether the Windows partition is primary or logical), and you can boot Windows directly from its own partition with Grub or some other decent boot loader.

---

### Post by ELF_O8 on 2008-12-26
It's true, the only problem people should find when installing Ubuntu after XP/Vista is one of their own fault: If you resize the NTFS partition so that you shrink *from the front of the partition* you risk offsetting the Windows bootloader and a having failed XP/Vista boots.
Other than that, I have never EVER experienced problems installing Ubuntu after Windows (and I've done it quite alot)

---

### Post by logos34 on 2008-12-26
right, windows wants a primary, but technically only the boot files need to have it.  And with just a little work windows will even boot directly from a logical. 

I've dual-booted XP x64 and XP Home on a logical and a primary no problem.  Now just for the heck of it I'd like to try booting XP from a external USB drive using this hack:

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

---

### Post by bliffle on 2008-12-26
I've had no problem installing ubuntu AFTER XP, but on this computer I've already installed ubuntu and I want to create an XP partition, too.

I have plenty of HDD space available in the last half of the HDD.

But I'm not sure how to proceed. I can allocate a partition easily enough, and even format it as FAT32. I can even label it as "boot" (but that takes "boot" away from the first partition where ubuntu is located).

But what then? If I mount the XP DVD/CD in the drive will it allow me to pick the partition?

Will the XP install allow me to install the boot records on the very first partition and then all the XP stuff out there in the wild blue yonder? I don't think so. I think I must move the boot stuff after the XP install.

---

### Post by logos34 on 2008-12-26
> **bliffle said:**
> 
But I'm not sure how to proceed. I can allocate a partition easily enough, and even format it as FAT32. I can even label it as "boot" (but that takes "boot" away from the first partition where ubuntu is located).

But what then? If I mount the XP DVD/CD in the drive will it allow me to pick the partition?

Will the XP install allow me to install the boot records on the very first partition and then all the XP stuff out there in the wild blue yonder? I don't think so. I think I must move the boot stuff after the XP install.

You're making this harder than it should be.

You don't need a separate boot partition for windows.  Just boot the XP install cd and point it at the space where you want it to go and format it.  (NTFS is preferable over fat32) 

The 'boot' label (*) is just a flag--it's only critical to have it on the XP partition when you're using the windows bootloader (which looks for an active primary partition).  Since you'll be using Grub I wouldn't sweat it (besides, your windows entry in menu.lst will probably have a 'makeactive' option)

---

### Post by bliffle on 2008-12-26
> **logos34 said:**
> You're making this harder than it should be.

You don't need a separate boot partition for windows.  Just boot the XP install cd and point it at the space where you want it to go and format it.  (NTFS is preferable over fat32) 

The 'boot' label (*) is just a flag--it's only critical to have it on the XP partition when you're using the windows bootloader (which looks for an active primary partition).  Since you'll be using Grub I wouldn't sweat it (besides, your windows entry in menu.lst will probably have a 'makeactive' option)

Sounds like I can go and do that right now! So all I hafta do to prepare is allocate a partition? Don't even have to format it?

---

### Post by logos34 on 2008-12-26
no, it can just be a blank space.  So basically either create a partition out of the unallocated space beforehand and format it, or leave it unallocated and let windows installer do it. (if the latter, do a regular vs. 'quick' format)

---

### Post by bliffle on 2008-12-29
logos,

That's what I did and the install went easily.

then I ran superGrub to test it.

Then I booted up ubuntu and modified /boot/grub/menu.lst to add the XP system and delete some archaic ubuntu kernels.

Now I have to add in all the network and wireless junk for the XP system, but it runs just fine, and I did many re-boots.

---

### Post by Mistoffeles on 2009-04-22
There is no need for XP to be in a bootable partition, primary partition, or any such thing. It will, however, not work from partitions outside of the range Microwhatsit recognizes (can't be on 5th or subsequent virtual partition in an extended partition, for example).

The reason most people put it on the first primary partition is that it's far easier than hand-tweaking GRUB (or whatever you wish to use) to bootstrap XP in some non-standard way, like from virtual partition 3 on the extended partition.

---

### Post by logos34 on 2009-04-22
> **Mistoffeles said:**
> It will, however, not work from partitions outside of the range Microwhatsit recognizes (can't be on 5th or subsequent virtual partition in an extended partition

actually it will work/boot from a logical partition *as long as the boot files are located on a primary partition* (e.g. a prexisting windows installation--which is how I had my dual-XP Home and 64-bit XP Pro setup), or else you manually tweak it.  But otherwise you're right.

---

