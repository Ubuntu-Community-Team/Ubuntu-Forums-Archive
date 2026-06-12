---
title: "Partitions resizing?"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by dr_psikick on 2006-05-10
I'm a totaly noob in linux, so be patience...
I have an 120 Gig HD.
   -Partition 1: Windows XP (+-104 Gig)
   -Partition 2: Ubuntu 5.10 (+- 15 Gig)
   -Free space (+- 1 Gig) I was planing to install Damn Small Linux...

But now i want to format the Windows partition to do a fresh install, and i want add more space to the Ubuntu partition. I only use Windows to play some games...

So i was planning to format the windows, make an smaller partition (+- 70 Gig) and then resize the Ubuntu partition with the rest of free space. Is this possible to do? I mean without making an new install of ubuntu? If so, someone can explain to me how i resize my Ubuntu from free space?

Thanks.

---

### Post by kb3hkg on 2006-05-10
As far as I know ext2/3 partitions cannot be resized but ntfs can, so your windows partition you can resize. I think you will have to reinstall ubuntu though, sorry.

---

### Post by aysiu on 2006-05-10
You can add space to the end of a partition but not the beginning of it.

---

### Post by syg00 on 2006-05-11
True - so, ....
You could free up some space, create a new part, move the current data, delete current part, then expand the new partition to fill the (now) empty space.

Lot of potential to screw things royally.

I usually advise people to just create a new partition, and mount it at some convenient mount-point (say /media/mp3s or similar), and allow it to fill up naturally. Simple, and minimum risk.

---

### Post by kb3hkg on 2006-05-11
You really are best off reformating. You can back up files to save a lot of your settings and such though if that is what you are worried about.

---

### Post by dr_psikick on 2006-05-11
Ok, thanks for the info. I'll format the entire disk and install both Win and Ubuntu

---

### Post by kb3hkg on 2006-05-11
of course make sure you install windows first. wouldn't want to have microsoft overwriting your bootloader.

---

### Post by az on 2006-05-11
[QUOTE=dr_psikick]I'm a totaly noob in linux, so be patience...
I have an 120 Gig HD.
   -Partition 1: Windows XP (+-104 Gig)
   -Partition 2: Ubuntu 5.10 (+- 15 Gig)
   -Free space (+- 1 Gig) I was planing to install Damn Small Linux...

But now i want to format the Windows partition to do a fresh install, and i want add more space to the Ubuntu partition. I only use Windows to play some games...

So i was planning to format the windows, make an smaller partition (+- 70 Gig) and then resize the Ubuntu partition with the rest of free space. Is this possible to do? [/QUOTE]

Sure.  You can boot a live cd, resize the current XP partition to 70 Gigs, provided you have the free space there.  Then you have a 34 gig chunk of free space.  You can simply move your current Ubuntu partition there (copy it), then delete the original partition and extend the ubuntu partition to eat the free space.  70 gigs for XP and 45 gigs for ubuntu.  Done.

There would be a problem if you wanted to shrink the XP partition down by less than 15 gigs - you would not have enough space to copy your ubuntu partition there.  You cannot move the beginning point of a partition, but you can copy it.  You just can't copy it onto itself.

---

### Post by kb3hkg on 2006-05-11
That would be what was suggested earlier and yes it would work. Unless you know exactly what you are doing though it leaves lots of room for dangerous errors. It is safer and easier probably to back up and reformat.

---

### Post by dr_psikick on 2006-05-13
[QUOTE=azz]Sure.  You can boot a live cd, resize the current XP partition to 70 Gigs, provided you have the free space there.  Then you have a 34 gig chunk of free space.  You can simply move your current Ubuntu partition there (copy it), then delete the original partition and extend the ubuntu partition to eat the free space.  70 gigs for XP and 45 gigs for ubuntu.  Done.

There would be a problem if you wanted to shrink the XP partition down by less than 15 gigs - you would not have enough space to copy your ubuntu partition there.  You cannot move the beginning point of a partition, but you can copy it.  You just can't copy it onto itself.[/QUOTE]

I'm not sure i understand (noob). How do i copy and extend the ubuntu partition? I would need to change Grub settings to, right?

---

### Post by az on 2006-05-13
[QUOTE=dr_psikick]I'm not sure i understand (noob). How do i copy and extend the ubuntu partition? I would need to change Grub settings to, right?[/QUOTE]
Not if you do what is described.  Once all is said and done, the partition names will be the same.

If you were to add another partition or remove the windows partition and the result would be that your linux partition would go from hda5 to hda6 or  from hda5 to hda1, then you would have to edit both grub menu.list and /etc/fstab accordingly, before you reboot.

---

### Post by morequarky on 2006-05-19
I could use some partition advise myself.

I have really messed up my partitions.

Here is the 411.  I love how I have formated my 80GB drive.  I would like to have more space in /var/www. 

I could do some resizing tricks which are of course dangerous.

I would like to backup all my data anyway, but I am skeptical as to how effective the backup will be.  "tar-ing" my whole drive throws errors and I have "simple backup config" configured but I don't know if it is configured correctly.  I never see it doing anything, so reinstalling really scares me, because I don't know if I have a backup file to work with.  I have installed and configured quite a lot of stuff and it would take me nearly a week to reinstall everything and get the server working again.

I am leaning towards just creating a new partition(if possible) and mounting /var/www to it, but I don't know if I can do that.

Anyways here is my partition table.  Maybe someone will have a creative solution to my situation.

---

### Post by syg00 on 2006-05-19
First, you can't "just add a partition" - I presume you are seeing that 74.56Gig, and figuring you still have a bit left out of your 80Gig.
Wrong. Marketing hype says 80*10^9 == 80Gig.
Where-as (80*10^9) / 1024 /1024 /1024 == ????.

You must have confidence in any backups before starting.
No confidence, no playing with partitions. Search here for backup threads - I've seen a couple lately.
Tar deals with filesystems - it needs to be pointed at partitions, not devices.

Remember if you do start toying with partitions, fstab may well require updating to accomodate.

---

### Post by morequarky on 2006-05-19
I was thinking along the lines of making /home or /fat32 smaller and pointing /var/www at the new partition.  And I would have to tweek fstab to do that.

---

### Post by syg00 on 2006-05-19
Fair enough. I've never had any luck resizing ext3 - you might do better.

If it was me, I'd ...
-copy all of hda10 to /home/holdit/ (create a new directory for it), and blow hda10 away. Gives you 8.5 Gig to play in.
- create an ext3 there,and copy *all* of /home across.
- blow hda9 away; now you have plenty of room to work with.
-set things up as you want, copy /home back, trash hda10 (in need).
- fix up fstab (and maybe Windows) 

All done.

Has to be done from a liveCD of course, but gives you a backup each step of the way, and doesn't require another disk.

---

### Post by dr_psikick on 2006-05-20
Just want to thanks to all the input i got. I dealed with the situation and my system is up again, but i did it the hard way, reinstalled everything...
Ubuntu is an easy OS to work with, but this community really helps.

---

