---
title: "Installation problem (Prepare Partitions)"
date: 2008-11-10
forum: General Help
---

### Post by iamBevan on 2008-11-10
I'll try and explain as thoroughly as I can:

Basically, I've taken an old HDD out of one of my computers to put into another one. On my old computer it was my secondary HDD.
    Now that it's in my other computer, i'm trying to use it as my only HDD. But when installing, i get to the Prepare Partitions stage and nothing in listed. But when i click Forward, i get the error "No root file system is defined.Please correct this from the partitioning menu"

Does anyone have any experience with this? Any help would be greatly appreciated.

---

### Post by CatKiller on 2008-11-10
Check your jumpers and cables. If the hard drive isn't detected by the BIOS, it won't be detected by Ubuntu, either.

---

### Post by iamBevan on 2008-11-10
It's detected by BIOS - and my jumpers and leads are 100% correct :)

---

### Post by ugm6hr on 2008-11-10
> **iamBevan said:**
> It's detected by BIOS - and my jumpers and leads are 100% correct :)

With the LiveCD booted, Go to GParted (System->Administration->Partition Editor).

Is the HD listed there?  If so - you should be able to create your partitions manually.

---

