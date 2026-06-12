---
title: "2 Grubs, 2 hdds, selectable boot from BIOS?"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by scottfmcleod on 2009-01-18
Hi all,

I've installed vista/ubuntu on a 500 gig drive that I have been using for a while now.  This hard drive has grub on it.

I later purchased a second hard drive (750 gig) to mess around with different linux distros and what not.  To make sure I didn't mess up my primary hard drive, I unplugged my 500gig and installed various linux/windows OSes on the 750.  This hard drive also has grub installed.

Currently, I have only booted with one hard drive plugged in at a time.  My question is, what will happen if I plug both hard drives in and turn on my computer.  Will I simply be able to select which hdd to boot from with my BIOS? (this configuration is what I'd prefer right now)  In the future, I will be able to switch to one hdd with OSes and the second for data - but right now I'm in school and don't want to spend the time / risk corrupting my configuration.

Thanks!

---

### Post by logos34 on 2009-01-18
shouldn't be a problem.  When you plug both drives in, select either one in the Bios as the boot device, that disk is seen as '(hd0)', just like before.  You can even add fstab entries/mount points in each of the linux OS's so you can access the others from any installation

---

### Post by Mark Phelps on 2009-01-19
You won't have a problem booting regardless of which drive you select as the default, but it you have more than one installation of Vista accessible, and you modify files in one Vista partition using the Vista running in the other Vista partition, don't be surprised if you get some file system corruption as a result.  Also, don't be surprised if, after you boot into the "second"  Vista, you discover that all your System Restore points in the "first" Vista have vanished -- and vice versa.

---

### Post by cariboo on 2009-01-19
I would suggest leaving the origional grub as it is, and use the configfile option in the grub that boots, usually the last installed. You would need to modify /boot/grub/menu.lst to look something like this:

```
title            Main System
root            (hd0,0)
configfile      /boot/grub/menu.lst
```

you will have to change root (hd0,0) to what ever the root of the drive that Vista/Ubuntu is installed. Using configfile means that whenever there is a kerenl update, you don't have to modify /boot/grub/menu.lst

The above entry should be added to the bottom of /boot/grub/menu.lst, and remove any entries pointing to other installations.

Jim

---

