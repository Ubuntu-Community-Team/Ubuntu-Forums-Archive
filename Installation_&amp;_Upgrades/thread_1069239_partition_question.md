---
title: "partition question"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Trim0 on 2009-02-13
sup guys
i'm installing ubuntu at this very moment, burned the image and everything and now i'm at the step where it says;
"prepare disk space"

now i've created an extra partition which is 40 gigs just for ubuntu and i want that partition to be the host of ubuntu.

these are the options which i'm unsure of..

1. guided - resize SCSI1
2. guided - use entire disk
3. manual

i selected manual but ubuntu labels the partitions in it's own way and the partition that i'm trying to use, according to ubuntu installer has like 3200 mb of used space, which doesn't seem right because i just created that thing and it's empty.

anyway, which option should i select in order to install ubuntu in the 40gig partition? 
i don't want to mess up the installer and i'll wait for somebody to answer so i can proceed with a proper installation...

---

### Post by Taemojitsu on 2009-02-13
I finally learned what the partition options are only recently.

Some useful links from Google 'ubuntu partitions':
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions) "Windows needs to be on a Primary partition"

basically, unless you want to allocate certain amounts of space for things like webserver caching or for personal files, (and assuming you don't want a separate 'boot' partition which I *think* makes it easier to have multiple Linux distributions at once), then you only need an Ext3 partition which maps to '/', and a Swap partition that is up to twice the size of your RAM (so maybe 6-8GB) that holds page files and for when your computer hibernates.

All the other options for locations make it so Ubuntu mounts a certain partition at a location in the [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) (note: I haven't read that article yet myself, lol), instead of mounting at a folder on the root (/) partition.

If you reinstall Ubuntu, unless you re-format the partition it only deletes system files, so your home directory and even many settings will be left untouched. which is nice. But you'll still want to back it up anyway, so... recommend just the Ext '/' and a swap partition.


Oh... and the Ext3 filesystem uses some space, I think. 3200 MB sounds high but ???. If it's not Ext3, it might be some other weird thing. Every file system does that tho, for example I tried formatting a thumb drive and FAT16 used maybe 100KB while FAT32 used >1MB for the file system. Ext3 is journaling so it tracks changes and maybe other stuff; tho 3200MB still sounds high.

btw one more thing: make sure you understand how GRUB works if you're dual-booting, lol. Don't do what I did and install Grub stage 1 on your Windows partition!! >_< (90% of the time Grub should go in the MBR, which is e.g. /dev/sda, compared to /dev/sda3 for a specific partition's boot record)

---

### Post by Trim0 on 2009-02-13
> **Taemojitsu said:**
> I finally learned what the partition options are only recently.

Some useful links from Google 'ubuntu partitions':
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions) "Windows needs to be on a Primary partition"

basically, unless you want to allocate certain amounts of space for things like webserver caching or for personal files, (and assuming you don't want a separate 'boot' partition which I *think* makes it easier to have multiple Linux distributions at once), then you only need an Ext3 partition which maps to '/', and a Swap partition that is up to twice the size of your RAM (so maybe 6-8GB) that holds page files and for when your computer hibernates.

All the other options for locations make it so Ubuntu mounts a certain partition at a location in the [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) (note: I haven't read that article yet myself, lol), instead of mounting at a folder on the root (/) partition.

If you reinstall Ubuntu, unless you re-format the partition it only deletes system files, so your home directory and even many settings will be left untouched. which is nice. But you'll still want to back it up anyway, so... recommend just the Ext '/' and a swap partition.


Oh... and the Ext3 filesystem uses some space, I think. 3200 MB sounds high but ???. If it's not Ext3, it might be some other weird thing. Every file system does that tho, for example I tried formatting a thumb drive and FAT16 used maybe 100KB while FAT32 used >1MB for the file system. Ext3 is journaling so it tracks changes and maybe other stuff; tho 3200MB still sounds high.

btw one more thing: make sure you understand how GRUB works if you're dual-booting, lol. Don't do what I did and install Grub stage 1 on your Windows partition!! >_< (90% of the time Grub should go in the MBR, which is e.g. /dev/sda, compared to /dev/sda3 for a specific partition's boot record)

ok, what if i want space for webserver caching, which do you think is the best option?
also, when i manually prepare with the partitions, i'm given with a couple of options (some of which you mentioned), what are the basic differences (without getting too complicated) between ntfs, fat32, ext3, ext2 etc???

---

### Post by Trim0 on 2009-02-13
i'm also not familiar with grub.
i simply burned the image, inserted the CD and i'm following instructions from the setup and you guys. lol

---

### Post by Pumalite on 2009-02-13
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Trim0 on 2009-02-13
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

just what i was looking for..
that's a lot of info but i think the basics of that manual will help me get started.
thanks

---

### Post by Trim0 on 2009-02-13
alright i'm using ext3, there's a checkbox about formating the partition. is it recommended to leave it unchecked or check it?

---

### Post by Taemojitsu on 2009-02-13
> **Trim0 said:**
> ok, what if i want space for webserver caching, which do you think is the best option?
also, when i manually prepare with the partitions, i'm given with a couple of options (some of which you mentioned), what are the basic differences (without getting too complicated) between ntfs, fat32, ext3, ext2 etc???
webserver caching is when you're HOSTING a webserver, and you want to make sure the entire drive doesn't get filled up with whatever files webservers have when they webserve

ntfs is the XP/Vista filesystem, that helps prevent errors.
FAT32 is the basic filesystem that everything can use, that is mostly used for thumbdrives that anyone can read. It has some limitations, like getting errors if you shut down while it's writing to the drive and it can't store files over 4GB (like DVD images).
ext3 is an extension of ext2, which gives it the same feature as ntfs of being able to prevent errors. It is the standard Linux filesystem for storing files.

The only other one you need for Ubuntu, besides the ext3, is the Swap filesystem which is just a chunk of blank space. (Windows has the same thing, but it's saved as a 3GB file in Vista instead of as a separate partition)


edit: if it's already in ext3, then NOT formatting it means that you'll keep files if you had a previous version of Ubuntu installed on it. Like you'd keep your Home directory. If you format it, you lose everything on it but if it's not ext3 already then you have to format it for it to work.

edit2: quick explanation of grub, because I feel like it ^_^ Your computer's BIOS checks if it's working, then looks in the Master Boot Record for a description of the partitions and how to boot up. If you only have windows, then the MBR just points to your windows partition. If you install Grub onto the MBR, then the MBR, or more specifically the Grub Stage 1 installed on the MBR, points at the Grub files (stage 2) on your Linux partition (or the /boot partition if you made it separate), which lists what operating systems you have on your system and which method to use to start them. If you select Windows it points at the same boot file that the MBR would. If you select Linux, then it starts loading the Linux kernel you selected, which is stored in the same /boot directory as Grub.

---

### Post by Pumalite on 2009-02-13
> **Trim0 said:**
> alright i'm using ext3, there's a checkbox about formating the partition. is it recommended to leave it unchecked or check it?

Format it

---

### Post by Trim0 on 2009-02-13
> **Taemojitsu said:**
> webserver caching is when you're HOSTING a webserver, and you want to make sure the entire drive doesn't get filled up with whatever files webservers have when they webserve

ntfs is the XP/Vista filesystem, that helps prevent errors.
FAT32 is the basic filesystem that everything can use, that is mostly used for thumbdrives that anyone can read. It has some limitations, like getting errors if you shut down while it's writing to the drive and it can't store files over 4GB (like DVD images).
ext3 is an extension of ext2, which gives it the same feature as ntfs of being able to prevent errors. It is the standard Linux filesystem for storing files.

The only other one you need for Ubuntu, besides the ext3, is the Swap filesystem which is just a chunk of blank space. (Windows has the same thing, but it's saved as a 3GB file in Vista instead of as a separate partition)


edit: if it's already in ext3, then NOT formatting it means that you'll keep files if you had a previous version of Ubuntu installed on it. Like you'd keep your Home directory. If you format it, you lose everything on it but if it's not ext3 already then you have to format it for it to work.

edit2: quick explanation of grub, because I feel like it ^_^ Your computer's BIOS checks if it's working, then looks in the Master Boot Record for a description of the partitions and how to boot up. If you only have windows, then the MBR just points to your windows partition. If you install Grub onto the MBR, then the MBR, or more specifically the Grub Stage 1 installed on the MBR, points at the Grub files (stage 2) on your Linux partition (or the /boot partition if you made it separate), which lists what operating systems you have on your system and which method to use to start them. If you select Windows it points at the same boot file that the MBR would. If you select Linux, then it starts loading the Linux kernel you selected, which is stored in the same /boot directory as Grub.

ok i see that you have a clear understanding of how this works.
is it a problem if I use the swap space in the C (vista) partition? according to the setup, i can't assign ext3 and swap in the same partition.

---

### Post by Taemojitsu on 2009-02-13
yes it's a problem. It will randomly write data all over your Vista partition, immediately breaking it.

Linux distros can share swap, because it's a separate partition. But Linux can't use the Swap file on the Windows partition that Vista uses for Swap. So you need to create a new swap partition, taking between 1x and 2x your RAM from the ext3 partition (resizing it, or just deleting it and creating a smaller ext3) and create a Swap partition with it.

---

### Post by Pumalite on 2009-02-13
There is a rule of 4 primary partitions per drive. You have to choose one and make it an extended partition; that way you can install '/' and /swap inside it.(2 logical partitions)

---

### Post by Trim0 on 2009-02-13
How much space does swap generally need?

---

### Post by Taemojitsu on 2009-02-13
up to 2x your RAM. If you have 4GB of RAM, you might want up to 8 GB of swap space. But this would only be used if you are using 4 GB of 'virtual RAM' (so a total of 8 GB being used, with that 4GB having been swapped out when you ran out of physical RAM) and then Hibernate which saves everything in RAM to the swap drive.

but that will hardly ever happen since you should never ever have 4GB swapped out or your system will be crazy slow doing anything; so you can get away with just a few GB of swap space or even less. If you don't have swap space it just means you have no 'virtual memory'.

---

### Post by Pumalite on 2009-02-13
1 GB in Desktops. 1.5 of your RAM in a laptop if you want to hibernate.

---

### Post by Trim0 on 2009-02-13
so should i quit the installer, and create a new partition for swap space?

---

### Post by Taemojitsu on 2009-02-13
I think the only reason to use Gparted (Admin => partitions in the LiveCD) instead of the installer-based partitions, if you want to set the partition Label to name it. :&#8203;P

You can create the swap partition inside of the installer by selecting 'manual partitions'
... i think

---

### Post by Trim0 on 2009-02-13
> **Taemojitsu said:**
> I think the only reason to use Gparted (Admin => partitions in the LiveCD) instead of the installer-based partitions, if you want to set the partition Label to name it. :&#8203;P

You can create the swap partition inside of the installer by selecting 'manual partitions'
... i think

i'm using the manual partitions option at this moment and i can't do that, thanks for your help BTW.

---

### Post by Taemojitsu on 2009-02-13
then you will have to cancel the installation like you said. The installation locks the drives, so other programs (like Gparted) can't access them.

(So go Admin \ Partition editor, and) it's probably faster to just delete the ext3 and create a new one, than it is to resize it. but i could be wrong. just be careful. :&#8203;p

---

### Post by Trim0 on 2009-02-13
> **Pumalite said:**
> 1 GB in Desktops. 1.5 of your RAM in a laptop if you want to hibernate.

i have 1gig of RAM on my laptop, so my swap partition should by 1.5gig? is it a problem if i assign more to it?
sorry for sounding so out of place, i just don't want to mess up the installer. on top of it, i really don't want to go back to windows.

---

### Post by Trim0 on 2009-02-13
on vista, i also have an partition which i keep to save some big files in case i reformat. can i use that partition for swap, even though there's files in it? or does the swap partition have to be completely empty as well?

*typed this in case you didn't see in previous page*

i have 1gig of RAM on my laptop, so my swap partition should by 1.5gig? **is it a problem if i assign more to it?**
sorry for sounding so out of place, i just don't want to mess up the installer. on top of it, i really don't want to go back to windows.

---

### Post by Trim0 on 2009-02-13
> **Taemojitsu said:**
> up to 2x your RAM. If you have 4GB of RAM, you might want up to 8 GB of swap space. But this would only be used if you are using 4 GB of 'virtual RAM' (so a total of 8 GB being used, with that 4GB having been swapped out when you ran out of physical RAM) and then Hibernate which saves everything in RAM to the swap drive.

but that will hardly ever happen since you should never ever have 4GB swapped out or your system will be crazy slow doing anything; so you can get away with just a few GB of swap space or even less. If you don't have swap space it just means you have no 'virtual memory'.

i don't fully understand this;
are you saying that assigning too much swap space can slow your system down?

---

### Post by logos34 on 2009-02-13
> **Trim0 said:**
> can i use that partition for swap, even though there's files in it?

yes, if you make what's called a swap **file**, as opposed to a swap partition which will format (erase) whatever is on it.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Taemojitsu on 2009-02-13
it won't fail or anything if it doesn't have 'enough' swap space. I actually don't know if/why 1x your RAM is the limit for paging files/'virtual memory'... but it won't fail the installer. If you have the space you could do it, but it won't improve performance and won't matter unless you actually use that much swap space. note that you can monitor swap usage in the system monitor, and also in the system monitor applet thing you can add to the gnome taskbar, to get a feel for how much swap you're using and how slow it gets if you use a lot of swap :&#8203;P


^ ... but swap files are for experts, and even thinking about it makes me anxious. i have enough problems setting things up as it is, i don't want to add extra work for something i could just set up during install lol.

---

### Post by Trim0 on 2009-02-14
thanks for your help guys, installation went perfect.

---

