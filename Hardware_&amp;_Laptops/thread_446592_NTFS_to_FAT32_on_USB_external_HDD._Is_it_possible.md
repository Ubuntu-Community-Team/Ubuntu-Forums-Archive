---
title: "NTFS to FAT32 on USB external HDD. Is it possible?"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by RyanVanDiemen on 2007-05-17
Hello, I have 320GB Toshiba USB hard drive. The thing is that it`s NTFS and everytime I want to move something from ubuntu to this disc I have to do it through windows fat32 partition. Is it possible to change partition to fat32 so I can write on it? Is it safe? Will there be any consequences (I don`t have any files larger than DVD iso 4,7gb)? Is it possible to do without moving data from the disc?

Thank you for the posts.

---

### Post by tturrisi on 2007-05-17
If you change the filesystem type you will lose all data on the disk.  Move the data to a dvd or another hard drive temporarily, change  the external drive to fat32, move the data back onto it.  If still have a xp system then connect the drive to it and use Disk Management to do the above.

---

### Post by RyanVanDiemen on 2007-05-17
Yes I still have WinXP, Disk management is some in-built application in WinXP? Never used it. I have Partition Magic though, but it`s old version 8.0 and I`m not able to change NTFS to FAT32 on this external drive using PM 8.0. I have about 200 gb on this drive and only 100gb of it on some dvds. Don`t want to spend the rest of the month backing-up the content, if you know what I mean...

---

### Post by kelvin spratt on 2007-05-17
i think you will find if you try to format to fat32 it will only format a small amount, you need to format with xpsp2 to get over this, you should be able to use disc management in xp if installed. it is much better to leave it as ntfs, install ntfs-3g and enable ntfs read and write. Fat32 is out dated is very hard on hdrives will only last a year or so.  i use 3 Hdrives and save everything in ntfs as that way it will always be accessible

---

### Post by RyanVanDiemen on 2007-05-17
Yeah, thanks. I`ve heard about ntfs-3g before, never tried it though. I think I will go that way. Thank you

---

### Post by Prometheus.172214 on 2007-05-17
NTFS cannot be downgraded to FAT 32, that said NTFS can still read FAT32 volumes due to partition magic. As mentioned above, if you really need to use a FAT32 volume, then backup you data from the NTFS drive to some other storage device and then format the volume into FAT32. Once this is done, you will have a drive with the FAT32 volume. In windows, click Start and select RUN and type in diskmgmt.msc and this will bring up disk management. The FAT32 volume should automaticallt start working when connected to a NTFS based Win XP computer. Here are a few links that tell you more about FAT 32 and NTFS. This is just for you to learn more about the Windows File Systems.

[http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx](http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx)

[http://www.theeldergeek.com/ntfs_or_fat32_file_system.htm](http://www.theeldergeek.com/ntfs_or_fat32_file_system.htm)

[https://www.microsoft.com/technet/prodtechnol/winxppro/maintain/convertfat.mspx](https://www.microsoft.com/technet/prodtechnol/winxppro/maintain/convertfat.mspx)

---

### Post by RyanVanDiemen on 2007-05-17
Thanks, I will definitely go with ntfs-3g. It there is solution to writing on ntfs I`ll do that. I don`t want to risk losing any data. Anyway I don`t think I will abandon windows in foreseeable future (unless I have 100 % replacement for all apps I need). Thanx guys.

---

### Post by Prometheus.172214 on 2007-05-17
> **RyanVanDiemen said:**
> Anyway I don`t think I will abandon windows in foreseeable future (unless I have 100 % replacement for all apps I need). Thanx guys.

Hmmm, so there are people like me, who cannot move away from Windows because of the programs they depend on...... Well I for one, sure hope we can get some apps from Windows ported to Linux.

---

### Post by RyanVanDiemen on 2007-05-18
Actually I have a list (my personal wishlist) of things I have to be able to do with Linux to definitely move away from windows. Even in the best case scenario, it will take at least year or two.  I don`t see Windows as badly as others in this community do. Yes it makes me sick quite often, yes I love Linux, it opened completely different world to me. But xp is actually quite good OS (not talking about safety), remember win98? And what about win95? Oh man, how they drove me mad... I don`t know about vista, never tried it and probably never will (maybe in work), but I just don`t believe that microsoft is trying to rule the world and tell us what to do. People are not sheep and they will always do what they want...

---

### Post by mgmiller on 2007-05-19
> (I don`t have any files larger than DVD iso 4,7gb)

This would be a show stopper for fat32.   ](*,) 
The largest single file you can put on a fat32 volume is 4 gb.  This is a major problem when using a drive for DVD iso storage.  You will need to stick with NTFS or EXT2/3 or reiserFS or similar for support of files larger than 4 gb.  There is a utility for windows that will let it read/write to an EXT2/3 volume, or you can go with ntfs-3g and just keep what you have.

---

### Post by RyanVanDiemen on 2007-05-21
> The largest single file you can put on a fat32 volume is 4 gb.

I thought it`s 5gb. In that case there`s nothing to think about. Thanx

---

