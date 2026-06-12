---
title: "Unable to mount USB (magicJack) PHONE"
date: 2008-05-26
forum: Hardware
---

### Post by Greedo on 2008-05-26
Since I've upgraded to Hardy I can no longer mount my MagicJack which connects from a USB port. (I was working on a way since the MagicJack isn't supported in Linux only Windows and MacOS to have it be recognized once I fired up VirtualBox)

The blue led lights up on the magicJack and when I look at the different drives - the drive PHONE appears on there, however it will not mount either at startup or by trying to manually mount the drive. 

When I looked at the details of the error this is what it was telling me:
mount_point can not contain characters: newline, G_DIR_Seperator (usually /)

I'm wondering if anyone has a solution to this problem (since I'm not the greatest hardware person) 

Maybe I would have to boot back up into my XP partition and take a look at the file structure on the magicJack USB drive and see if the one of the files starts with a slash? I'm also not sure about renaming some of those files since it might effect the autorun.ini and the other main programs which make the VOIP software run since they probablly have internal pointers to those directories

suggestions anyone???

---

### Post by Greedo on 2008-05-26
Just as a note - before I upgraded to Hardy, Gutsy was able to mount this USB volume, and that's somewhat what I'm not understanding

---

### Post by Greedo on 2008-05-27
Trying to solve this problem, I booted back into my windows XP partition (where the usb drive works) and then explored the drive. The drive name in windows explorer is magicJack - yet in ubuntu looking at it under computer it says PHONE (and is unmountable) 

I tried to rename the drive but it told me that I could not rename an unmountable drive. Anyone know how to maybe rename this to what is being recoginzed in the windows explorer? 

Like I said I'm trying to first mount this volume and then see it in virtualBox. 

thanks.

---

