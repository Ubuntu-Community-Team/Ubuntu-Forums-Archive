---
title: "Different ubuntu versions in dual boot?"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by kalle314 on 2005-12-23
If this has already been discussed, please point me to that discussion!

The thing I want to do is to get Dapper Drake and have it along with my current Ubuntu version (in different partitions?) in dual boot together with Windows.
When the official release if Dapper comes, I would like to have only one Ubuntu partition.

Is this easy to do?
Do I just follow the automatic installation process, or is there something i ought to know?
What will happen to Grub when I install a second Ubuntu version?

Edit:&#12288;Sorry, I said BIOS when I meant Grub.

---

### Post by kwaanens on 2005-12-23
I've been running a triboot with FC4, Ubuntu and XP. That worked fine.

You need to manually partition your system, and Ubuntu probably won't see your other ubuntu installation, so you need to  manually edit /boot/grub/menu.lst

I never got Ubuntu and FC4 to talk to each other on all areas. For instance, when trying to share all Thunderbird user files, Ubuntus Thunderbird never worked.
You should *not*, under any circumstances share the your /home/user-folder across different versions of Ubuntu. That *will* be disaster.

- Ketil

Edit: BIOS will not be affected either way. Ubuntu doesn't edit BIOS, which is the way it has to be.

---

### Post by kalle314 on 2005-12-23
Thanks, 

but will Grub be installed again when I install Dapper Drake, or will my old Grub still be in charge of boot loading?

Will there be any problem when I want to merge the two Ubuntu partitions in april?

---

### Post by kwaanens on 2005-12-23
That's true. I used to have two grubs, one on MBR and one that Fedora took care of.

You need to check this (ie. tick or untick) the box in your new installation.

You should the MBR-Grub with entries for XP and Breezy, and have an antry which forwards you to the new Grub, making Dapper boot.

Doing it this way, you won't have to manually edit any menu-lst if you upgrade your kernel.

- Ketil

---

