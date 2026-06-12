---
title: "copy to new harddrive?"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by wormeyman on 2005-04-27
I installed ubuntu on a (test) 4gb hard drive and have promptly filled it up, how do i move my files/settings over to a new hard drive?

Will i have to re-do Grub?

---

### Post by Xerampelinae on 2005-04-27
[QUOTE=wormeyman]I installed ubuntu on a (test) 4gb hard drive and have promptly filled it up, how do i move my files/settings over to a new hard drive?

Will i have to re-do Grub?[/QUOTE]
 ```
cp -a /mnt/old_drive /mnt/new_drive
```
This should do it, although I haven't tried it myself.  It requires both hdds be in the machine at the same time, and mounted in the obvious places in that command.

You'll have to reinstall grub in the mbr, but that's no problem.  Assuming your new root partition is on the slave hard drive, 3rd partition you would do
```

sudo grub
grub>root (hd1,2)
grub>setup (hd1)
grub>quit

```

---

### Post by wormeyman on 2005-04-27
Wouldn't i have to format it first?

---

### Post by Xerampelinae on 2005-04-27
Well, yes of course... you have to create partitions with fdisk and then use the mkfs.xxx programs...

If you're not sure of what you are doing, it might be easiest to just re-install ubuntu on the other hdd, and only copy your home directory, which contains all your personal files and user configuration files.  It would miss system configuration changes, but those are easy to replace generally.

---

### Post by wormeyman on 2005-04-27
[QUOTE=Xerampelinae]Well, yes of course... you have to create partitions with fdisk and then use the mkfs.xxx programs...

If you're not sure of what you are doing, it might be easiest to just re-install ubuntu on the other hdd, and only copy your home directory, which contains all your personal files and user configuration files.  It would miss system configuration changes, but those are easy to replace generally.[/QUOTE]
 Yeah that is what i'm starting to think.

---

### Post by Xerampelinae on 2005-04-27
[QUOTE=wormeyman]Yeah that is what i'm starting to think.[/QUOTE]
 Well, give it some more time and someone may post another way.  

It could perhaps be done with dd very easily, but I've never tried it and there may be some special things you have to take into consideration since the two disks are different sizes..

---

