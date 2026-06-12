---
title: "Gparted Live will not load"
date: 2008-10-12
forum: General Help
---

### Post by Jeztastic on 2008-10-12
Hi,

I am currently running Ubuntu and XP, with a shared ext3 Home partition. XP is having loads of problems with the ext3 partition, so I am trying to reformat it as NTFS. However, I can't get Gparted Live to load. It recognises it on boot, but then hangs on a black screen. I have made a couple of Live CDs, and checked them for errors.

Is there another way to do this?

Thanks,

Jez

---

### Post by mike555 on 2008-10-12
Your Ubuntu CD has gparted on it, just use it ..... your gparted live disk may not have graphic drivers for your system ....

---

### Post by Topsiho on 2008-10-12
For some reason the new GParted Live CD's don't work here either.
But, as Mike555 said, the Ubuntu Live CD has GParted on it which you can use.

In stead of NTFS it is maybe better to use vfat. Correct me if I am wrong, but in Linux one can read NTFS files, but to write them is not possible without some dedicated software (I forgot which, but see Synaptic).

Hope this helps,

Topsiho

---

### Post by sisco311 on 2008-10-12
> **Topsiho said:**
> 
In stead of NTFS it is maybe better to use vfat. Correct me if I am wrong, but in Linux one can read NTFS files, but to write them is not possible without some dedicated software (I forgot which, but see Synaptic).

Hope this helps,

Topsiho

In hardy you can read/write ntfs partitions.
The ntfs-3g driver is installed by default.

---

### Post by eXonius on 2008-10-12
I'm not very good at this, but, shouldn't he be able to reformat the partion within Windows XP? :-k

EDIT: Within XP go to Control panel - administrative tools - computer management - disk management. The ext3 partion might show up as beeing an unknown format. But you should be able to reformat it to NTFS. Remember all data will be removed :D

This is the solution someone else told in a post here: [http://forums.linksys.com/linksys/board/message?board.id=Network_Storage&message.id=134](http://forums.linksys.com/linksys/board/message?board.id=Network_Storage&message.id=134)

---

### Post by Jeztastic on 2008-10-12
I downloaded gparted from synaptic, but when I tried using it, all the options and menus were greyed out. How do I use gparted from the ubuntu CD. Is there an option to boot into it?

I've had less problems reading and writing to NTFS from Linux than ext to XP.

---

### Post by eXonius on 2008-10-12
> **Jeztastic said:**
> I downloaded gparted from synaptic, but when I tried using it, all the options and menus were greyed out. How do I use gparted from the ubuntu CD. Is there an option to boot into it?

I've had less problems reading and writing to NTFS from Linux than ext to XP.

But have you tried what i added? Or did I misunderstood what you were going to do? X)

---

### Post by Jeztastic on 2008-10-12
no, missed your edit. Will try, though I have heard bad things about XP's format program.

---

### Post by eXonius on 2008-10-12
> **Jeztastic said:**
> no, missed your edit. Will try, though I have heard bad things about XP's format program.

Okay, let me know how it worked O:)

---

### Post by louieb on 2008-10-12
> **Jeztastic said:**
> ... XP is having loads of problems with the ext3 partition, so I am trying to reformat it as NTFS....

Be careful here if you reformat your Ubuntu root partition you will kill GRUB and the computer won't boot. And if you reformat your home partition the computer will boot but Ubuntu will not work excerpt in recovery mode.

Please post your partition table by copying the output of
```
sudo fdisk -l
```
and the output of ```

mount
```

---

### Post by Jeztastic on 2008-10-12
> **louieb said:**
> Be careful here if you reformat your Ubuntu root partition you will kill GRUB and the computer won't boot. And if you reformat your home partition the computer will boot but Ubuntu will not work excerpt in recovery mode.

Please post your partition table by copying the output of
```
sudo fdisk -l
```
and the output of ```

mount
```

Ah... Just saw that a leetle bit too late! :mad:

Just formatted the home partition, and the XP formatter left me just over a GB unformatted. That went well!

---

### Post by eXonius on 2008-10-13
> **Jeztastic said:**
> Ah... Just saw that a leetle bit too late! :mad:

Just formatted the home partition, and the XP formatter left me just over a GB unformatted. That went well!

My bad? very sorry about this :(

---

