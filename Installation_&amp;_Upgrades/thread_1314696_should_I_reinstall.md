---
title: "should I reinstall"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by PsYcHoTiC_MaDmAn on 2009-11-04
currently using EXT3 and 9.10.

however boot speeds are much lower in 9.10 than they were in 9.04. been thinking about a reinstall anyway, in that I create a /home partition, and then a partition for Ubuntu, thereby leaving it open to try other distros with little hassle. 

so would it be worth making a Gparted disk, resizing the partition and creating a /home partition (EXT3 to avoid the corruption issues) then coping over the /home folder.

after that wiping the main folder, creating a partition for ubuntu in EXT4.

it's also a good opportunity to completely remove wine, cause I cant seem to get rid of all the files via sudo apt-get purge wine (to do a clean reinstall)

would you bother redoing it??

---

### Post by jjcv on 2009-11-05
> **PsYcHoTiC_MaDmAn said:**
> 
would you bother redoing it??

I did.

I initially upgraded to the 9.10beta.

Once 9.10 was released I repartitioned (much as you suggested).   I like to do a clean-out occasionally and also like to keep /home separate for later installs.

It is easy enough if you keep a copy of /home/yourname and then you can selectively copy what you want to keep or just copy the whole lot over and you are back with your old desktop.

It's amazing how quickly one gathers a pile of junk on their systems. :p

---

### Post by PsYcHoTiC_MaDmAn on 2009-11-07
did the reinstall, just need to transfer all user data over. 

massive improvement in boot ups however, down to about 25 seconds, got to find the bootup tweaks again to try and get it faster still.

but as a note, anyone wanting to speed up the boot, consider using EXT4 even if its just for the system folders, (I'm going to stick with EXT3 for data, atleast for now.)

---

