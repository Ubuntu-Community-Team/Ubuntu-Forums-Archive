---
title: "Plan to Install 9.10...  what to back up?"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Dullstar on 2009-10-18
I need to know which directories to back up to easily restore my configuration from 9.04 when I install 9.10.

---

### Post by mikewhatever on 2009-10-18
I'd recommend backing up all of the home directory, which usually contains your files and settings.

---

### Post by Dullstar on 2009-10-18
is this all I need to back up?
P.S. is there a way I can just assign it to its own partition?  I've heard it can be done, but I don't know how.

---

### Post by stinger30au on 2009-10-18
backup your email, this is easy if u use evolution hit file backup

backup your firefox favourites

everything else you have saved to the boot hdd needs to be backup too

---

### Post by Dullstar on 2009-10-18
I actually don't use mail clients.  I use the built in interface on gmail, and I don't mind it at all, because I feel it's awfully easy to use, but the customization is great.

About Firefox favourites:  where are they stored?

---

### Post by Dullstar on 2009-10-18
Sorry to double post, but I also want to know if it is possible to make a home folder partition, and share it between multiple distributions.

---

### Post by earthpigg on 2009-10-18
firefox settings are kept in /home with just about everything else. specifically, firefox stuff is kept in ~/.mozilla .

specifically, open the file manager and select view -> hidden files. then look at all the files/folders starting with a period in your home directory. these are called 'dotfiles' and store settings and whatnot.

for a seperate home partition:

while doing a fresh install of 9.10, select 'manually partition'.

leave your swap partition alone, except 'use as' to be 'swap area'.

delete the other partition.

create a 10-20gb partition with the 'bootable' flag, 'ext4', and a mount point of '/'. format: yes. that will be your 'root partition'.

with the rest of your space, create an 'ext4' partition with the mount point of '/home'. format: yes. that will be your 'home partition'.


as for sharing between distributions... yes it is possible, but don't be surprised if a few applications act funny from time to time because they have different versions of the same program, and the old version can't read the new version's dotfiles.

when installing the new distro, give it it's own / partition, and set your home partition's mount point to be /home. select 'no, do not format this partition.'

there is no guarantee that your 2nd distro of choice will give you that option.

---

### Post by mikewhatever on 2009-10-18
> **Dullstar said:**
> is this all I need to back up?
P.S. is there a way I can just assign it to its own partition?  I've heard it can be done, but I don't know how.

You'd have to go with manual partitioning, create a partition and assign the /home mount point to it.
Generally speaking, it's a good idea to backup whatever you don't want to loose.

---

### Post by Dullstar on 2009-10-18
Distros of choice:

Gentoo
Puppy
Ubuntu 9.10

---

### Post by Dullstar on 2009-10-19
O_o
:mad:

That's the first time you've failed me, UNetbootin!
Why won't PartedMagic go onto that flash drive?!  Wait, didn't I back up the data on that thing?  So WHY DON'T I JUST REFORMAT IT?

---

