---
title: "Uninstall Linux Mint"
date: 2008-07-30
forum: General Help
---

### Post by MiniK on 2008-07-30
Hey. I've got Linux Mint on a seperate partition to Windows XP and I was wondering if there's any way to completely remove Linux Mint so that there's just Windows XP?

Please don't say just delete the partition because I've tried it before and have had my system completely break - GRUB error or something on boot. I also don't have the Windows disc handy so I've got one shot at this.

Please help,

Ryan

---

### Post by paul101 on 2008-07-30
ok, you'll need to delete the partition ( :razz: ) and use the xp disk to restore the winduhs boot loader (which you dont have)


can you borrow an expee disk from someone?

---

### Post by tamoneya on 2008-07-30
deleting the partition is how it is done.  You just need to use the XP install disc in order to fix the MBR and set it back how it was before grub was there.

---

### Post by tuxxy on 2008-07-30
> Please don't say just delete the partition because I've tried it before 

erm delete it :lolflag:

---

### Post by OutOfReach on 2008-07-30
Deleting the partition is the only way that I can think of to remove any OS.

---

### Post by SunnyRabbiera on 2008-07-30
Well why?
Mint has a lot of features built in and such so that a windows user can understand it, what is your trouble?

---

### Post by ByteJuggler on 2008-07-30
OK, you need to delete the partition, then boot with the XP CD, into recovery console, then use
```
fixmbr
fixboot
```

That should restore your XP boot sector and allow XP to boot.  If you have further problems please post back. (That's off the top of my head etc.)

Aside: You probably would want to also resize the XP partition to use the freed Ubuntu Mint space.  XP isn't capable of doing that, but you might get away with GPartEd....

---

### Post by mordak13 on 2008-07-30
If you can choose to boot to an admin console in XP hit eithr F5 or F8 can't remember which, then type: fixmbr that will do what it says. Then you should be able to reformat the partition from within the Windows Disk Management controls somewhere. It's been a while so I can't remember it all. I've done this in the past but like I said it's been a while.

ETA: Backup your XP stuff incase you hose the drive trying to resize any of the partitions.

---

### Post by Oldsoldier2003 on 2008-07-30
Download and burn a supergrub disk. Once you've deleted the mint partition you can use the supergrub cd to restore your windows mbr. (since all of the posters so far have ignored the fact that you don't have the xp cd.)

---

### Post by maughansterman on 2008-07-30
Mint is a great program

---

### Post by demios on 2008-07-31
k supposing one wanted to get rid of linux and keep the partition, would simply formatting the partition work, or would the dual boot prompt still show on startup?

---

### Post by jocko on 2008-07-31
> **demios said:**
> k supposing one wanted to get rid of linux and keep the partition, would simply formatting the partition work, or would the dual boot prompt still show on startup?
You would get a grub error.
The initial part of grub is installed in your disks mbr (master boot record) and the rest is in the /boot/grub folder in your mint partition. If you format the mint partition, the part of grub that is in the mbr will still be there but it won't be able to find the rest of the grub files.

You need to restore the windows mbr, so that your computer will load the windows boot loader directly.
I suggest you get a [Super Grub Disk]("http://www.supergrubdisk.org/") and use it to restore the mbr, and then you can delete and reformat the linux partition.

---

### Post by MiniK on 2008-07-31
> **Oldsoldier2003 said:**
> Download and burn a supergrub disk. Once you've deleted the mint partition you can use the supergrub cd to restore your windows mbr. (since all of the posters so far have ignored the fact that you don't have the xp cd.)

Thank you SO much! First I ran the Ubuntu Live CD and tried to delete the partitions but it didn't work so I grabbed my Vista Anytime Upgrade CD and used their powerful partition formatter/deleter to delete the partitions. I booted back into the Ubuntu Live CD and made the Windows partition fill up all of the space. I ran the supergrub CD and fixed Windows and it's working fine! Thanks a lot. :)

---

### Post by demios on 2008-08-02
> **jocko said:**
> You would get a grub error.
The initial part of grub is installed in your disks mbr (master boot record) and the rest is in the /boot/grub folder in your mint partition. If you format the mint partition, the part of grub that is in the mbr will still be there but it won't be able to find the rest of the grub files.

You need to restore the windows mbr, so that your computer will load the windows boot loader directly.
I suggest you get a [Super Grub Disk]("http://www.supergrubdisk.org/") and use it to restore the mbr, and then you can delete and reformat the linux partition.

right so I run the super grub disk first, then format the partition? thanks man.

[edit] simply installing hardy over the old version worked for me, but I'll keep the disc. thanks again.

---

