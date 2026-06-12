---
title: "Best way to Partition Ubuntu"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by dj-toonz on 2009-10-12
Hi all, when Karmic 9.10 comes out as stable I'm going to be downloading the .iso file & doing a clean install over Jaunty. at the moment I've got the whole hard drive taken up. What's the best way to Partition the drives as on the desktop I've got eight 2 TB drives (all the drives are set up in raid 0 mode)  & 12 gigs of ram (somebody said I don't need to use a swap drive with that amount of ram) is that true under Linux?, I want to use ext4 & encrypt the home drive.

this is how I would like to Partition the system

/ for the applications
/home for my files
/tmp for temporary files
/swap (but I don't know if that's needed with having 12gigs of ram ((going to be upgrading it soon tho to 16gigs))

so how would you Partition the system like that as I've never done any Partitioning before under Linux :-( as I've always let the installer do it for me 

cheers

---

### Post by Atten-dev on 2009-10-12
It would probably be easier to do all this if you use the alternate install CD... its much happier with unusual hard-disk/partition setups.

If you have hardware raid 0, essentially what you'll do is choose Manual Partitioning when the installer asks and create 4 partitions and mount them under /, /home, /temp and use one as swap. I have never encrypted a home directory from the alternate installer, but if I remember correctly, you might need use LVM to encrypt it.

If you do not have hardware raid 0, you will create partitions on each of your drives, and set them to be used for RAID and then once you have added them all to a raid array, proceed as above on the raided space.

I doubt you'd need swap. I've got 8Gb and have never noticed it being used. In Windows I know you can not use page file if you've got that much ram, and I would assume it would be the same for linux, but I have never tried an install without it. I usually just set it to 1 or 2 Gb.

---

