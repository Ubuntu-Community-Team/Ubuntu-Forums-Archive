---
title: "Multiple Distros"
date: 2008-08-15
forum: General Help
---

### Post by Zopiac on 2008-08-15
I want to install various linux distros; how would i go about doing that? i have ubuntu, xubuntu, and kubuntu, but i want to also add on opensuse, mandriva, etc. but i dont know how. is it possible? can i have a grub menu like thing for choosing which distro i want to use, or what?

---

### Post by tuxxy on 2008-08-15
Yes you can install multiple OS's, have you thought about using virtualbox and testing some, then you know which ones you prob like.

---

### Post by Zopiac on 2008-08-15
> **tuxxy said:**
> Yes you can install multiple OS's, have you thought about using virtualbox and testing some, then you know which ones you prob like.

i have been using a ton of 8GB hard drives i have left over from my old school to test them and using live cds etc (am burning iopensuse right now) so i know (or will know) which i want, but i dont understnd how to install multiple distros on one computer/hard drive

---

### Post by Too Late on 2008-08-15
Installing multiple linux distros in one machine is not an issue.

You just have to be careful not to destroy your existing partitions during install. It may be a good idea to clear up some space (resize current partitions) before starting installation.

Also, many distros install the grub to the MBR by default. You may want to change this, if you want to continue using the current grub (and its menu.lst file). Then you must manually adding your new distros to the grub menu. You can also install grub bootloader in the beginning of the new partitions, after that you can use chainloading. Having a separate boot partition for grub can be useful.

Different distros can normally use the same swap partition, but I don't know about the special cases, like having the hibernation file saved there (?).

---

### Post by snowpine on 2008-08-15
> **Zopiac said:**
> I want to install various linux distros; how would i go about doing that? i have ubuntu, xubuntu, and kubuntu, but i want to also add on opensuse, mandriva, etc. but i dont know how. is it possible? can i have a grub menu like thing for choosing which distro i want to use, or what?

Xubuntu, Ubuntu, and Kubuntu can all be installed together on the same partition; you just choose which you want from the Sessions menu each time you log in.

I would highly recommend installing VBox or VMware so that you can try the different distros in virtual machines.

Good luck!

---

### Post by Zopiac on 2008-08-15
> **Too Late said:**
> You just have to be careful not to destroy your existing partitions during install. It may be a good idea to clear up some space (resize current partitions) before starting installation.

It would just be an install option?

I need a separate partition for each distro, i bet (besides the k/x/ubuntu)?

---

### Post by snowpine on 2008-08-15
> **Zopiac said:**
> It would just be an install option?

I need a separate partition for each distro, i bet (besides the k/x/ubuntu)?

Yes, a separate partition for each distro, plus a swap partition, and I would also recommend one more partition for data you want to share between the distros.

---

### Post by Too Late on 2008-08-15
Yes, you need a separate root partition for each distro.

Some distros have very good partitioning tools at the install stage, while some others can do almost nothing. Therefore, it would be wise to shrink partitions (if there is no empty space now), and possibly even make new ones, before starting.

---

### Post by BarryMaccaukner on 2008-08-15
Yes and remember you can only have 4 partitions on the hard drive so you could only have 3 seperate os's. If you want Windows on there make sure to install it first because boot.ini will wipe out grub, so if you install fedora then xp , you won't be able to find fedora.

---

### Post by RATM_Owns on 2008-08-15
You could boot into Windows and add Ubuntu to the boot list.
Or boot into the Ubuntu Live CD and reinstall GRUB.

You can only have 4 physical partitions but as I remember, infinity logical partitions, provided you have enough hard drive space.

---

### Post by snowpine on 2008-08-15
> **BarryMaccaukner said:**
> Yes and remember you can only have 4 partitions on the hard drive so you could only have 3 seperate os's. If you want Windows on there make sure to install it first because boot.ini will wipe out grub, so if you install fedora then xp , you won't be able to find fedora.

This is not true. You can have more than 4 partitions if you set them up as logical partitions.

I stand by my original advice to just use virtualization.

---

### Post by Zopiac on 2008-08-16
<HINT>

I want bill gates to die, and windows with him, so i dont need a partition for window$ ;)

---

