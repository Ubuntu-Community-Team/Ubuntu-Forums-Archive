---
title: "Formatting a USB mobile hard disk"
date: 2005-11-23
forum: General Help
---

### Post by WebDrake on 2005-11-23
Hello all,

I have a USB hard disk, capacity 80GB, that I would like to format in ext2 or ext3.  The aim here is to get a disk to store large data files which I can use under both Linux and Windows (although the latter obviously requires a special driver installed to work with the ext3 filesystem).

I don't currently have Linux installed on any of my systems but, by booting from the Ubuntu 5.10 Live CD, I can get a basic version of Breezy Badger up and running. Then, if I go to System -> Administration -> Disks, it detects the USB drive as /dev/sda1/ with filesystem "Unformatted" (just as you would expect ;) ).

If I click on the "Format" button, I am asked for a format type---obviously extended 2 or extended 3, and I will probably go for the latter---but also an access path, e.g. boot/, home/, mnt/, tmp/ etc. What should I select, bearing in mind this USB drive is just going to be for storing data files, and that I want it to work like just another disk drive?

[The latter question may show the Windows influence on me, so any education is welcome. ;)  Basically I want something that either under Ubuntu or Windows I can access, read and write to with an absolute minimum of fuss.]

Many thanks,

-- Joe

---

### Post by apollo2011 on 2005-11-23
The access path is simply a location that the drive will be mounted on Linux so you can access the files on it and write new files to it. Unlike Windows, where the drive gets mounted at C: or D: etc.  Linux lets you put it into any folder, as long as that folder does not exist on the / partition already.  Since you are on a Live CD, this doesn't matter, because as soon as you reboot, this setting will be lost.  You are best off using the /mnt/ directory.

---

### Post by WebDrake on 2005-11-23
Thanks very much.  It's all working according to plan now! :-)

---

### Post by soulestream on 2005-11-23
if you wanted little amount of fuss why not just format it fat32, that way linux and windows can see it with no special hardware needed.


soule

---

### Post by WebDrake on 2005-11-23
[QUOTE=soulestream]if you wanted little amount of fuss why not just format it fat32, that way linux and windows can see it with no special hardware needed.[/QUOTE]
True.  Well, initially I didn't because when I first tried to format the drive---via Windows XP Pro---it only gave me the option of NTFS.  Then, using an Ubuntu Live CD, the default option was ext2.  And having seen that, I thought, the hell with it, it's a superior filesystem to FAT32 and I can get Windows to deal with it, so why not?

If I was going to be taking around this USB drive plugging it into every Windows machine I encountered, I would have thought differently, but as it is, ext3 seems a perfectly good choice.

Lest you query why I had to use a Live CD, it's because right now I only have XP Pro on my machine.  Getting about 33GB of files off the internal hard disk is the first step in slimming things down so I can resize the NTFS partition and make room for an Ubuntu install. ;-)

---

