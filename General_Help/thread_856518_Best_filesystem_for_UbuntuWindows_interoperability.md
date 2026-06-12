---
title: "Best filesystem for Ubuntu/Windows interoperability"
date: 2008-07-11
forum: General Help
---

### Post by 5circles on 2008-07-11
I'm trying to use an external drive, connected via USB, as a backup for network storage.  I want to be able to move the drive to different systems so that I can maintain access while other cleanup is being done.

After formatting as FAT32 and starting the mirror I realized that it won't work because some of my files are too large.  I'd previously had mixed results with NTFS and EXT2 or EXT3, but it looks like I have to go back to using one of them.

What's the current state of drivers for NTFS, EXT2, EXT3?  
[LIST]
[*]Can I safely use an NTFS drive on Ubuntu to read and write?
[*]Is ext2ifs the best application to use on Windows (Vista and/or XP)?
[*]Can I preserve access timestamps?  (I don't care as much about permissions)?
[/LIST]

Thanks!
Mike

---

### Post by rbprogrammer on 2008-07-11
> 
[LIST]
What's the current state of drivers for NTFS, EXT2, EXT3?
    * Can I safely use an NTFS drive on Ubuntu to read and write?
    * Is ext2ifs the best application to use on Windows (Vista and/or XP)?
    * Can I preserve access timestamps? (I don't care as much about permissions)?
[/LIST]

First off, I am in no way an expert on this.  But I think I can help you find your answers.
[LIST]
[*]ntfs-3g is a driver for read/write on NTFS formatted drives/partitions
[*]ext2ifs may not be perfect (eg. will not maintain journal in EXT3 formatted drives) but as far as I know it is the best out there.
[*]timestamps?  That would probably depend on the driver.
[/LIST]

These websites will help you get more info on the abilities/inabilities of the drivers:
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) -> [http://www.ntfs-3g.org/support.html#questions](http://www.ntfs-3g.org/support.html#questions)
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) -> [http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

Chances are since NTFS is not designed for Linux, and EXT2/EXT3 are not designed for Windows, your probably not going to get every feature available within the other operating system.

I have never written to an NTFS partition from Linux, but I do however use the ext2ifs driver all the time for my external hard-drive.  Its formatted as EXT3, but the driver only mounts the drive as ext2.  So it doesn't maintain the journal and if there are journal errors, I would then need to fsck the drive in Linux.

Hope that helps at least a bit :guitar:

---

### Post by 5circles on 2008-07-11
Thanks!  I think you've confirmed both the current status and the general point that a file system originating on Linux is more likely to have better support.  I've reformatted as ext2 and restarted the mirror.  Perhaps I should have used ext3, but I wanted to get this first mirror done quickly so I can clean up the NAS.

---

### Post by coffeecat on 2008-07-11
Which version of Ubuntu are you using? NTFS read-write works out of the box (using the ntfs-3g driver) in Ubuntu 8.04. If you plug in a USB drive formatted NTFS it should automount with no problems. As far as I can make out, the ntfs-3g driver is now reliable and you should have no more problems with NTFS than when using Windows. I use it for Windows/Ubuntu compatibilty and haven't had any problems yet.

Timestamps are preserved now that the Nautilus 2.22 bug has been fixed in Ubuntu (which is more than can be said for some other distros :roll: ). You may not have noticed, but for some time timestamps were not preserved when doing drag and drop copies using Nautilus. This was true whatever filesystem was involved - fat32, ext3, ntfs.

To be honest, as a single-user I find permissions a damn nuisance with external drives, and the lack of support for Unix permissions in NTFS is a positive blessing for me. But I see that's not an issue for you. I was wanting to copy some very big files (>4 Gb) from my Mac to Linux. So I formatted an external drive as hfs+ with the Mac (the Mac filesystem can be read in Linux), copied the files and plugged the drive into my Linux box. It automounted fine, I could read the root directory fine, but I could not browse into sub-folders. :-k Then I realised why. Mac OS uses Unix permissions just like Linux, but my UID on my Mac is different from my UID in Ubuntu. Grrr. I had to browse the drive as root, copy the files and then chown them back to my ownership. Grrrrrrrr. :wink:

---

### Post by 5circles on 2008-07-11
Thanks for the additional information.  I wish I'd tried Ubuntu before I reformatted the drive from NTFS to FAT32.  Now I'm on ext2 and probably don't need to change again - except that using NTFS would probably avoid the need to install ext2ifs on other systems.  I'm on Ubuntu 8.04, so it sounds like NTFS would work.

When I said I don't care about permissions it seems like I'm in a similar situation to you in that I can access as root (or an administrator) if necessary.  But it is sometimes annoying.  I'm not very experienced at the Ubuntu style of getting to root access.  I presume that I can just start a separate copy of an application (Nautilus for example) with sudo and then I'll have full permissions.

---

### Post by avtolle on 2008-07-11
You should start Nautilus or any other graphic application from the command line with gksudo or gksu, to avoid some possible not so nice issues in the future. Back in a moment with a link.

EDIT: Give this a read: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by 5circles on 2008-07-11
Thanks - I always wondered about starting graphical apps from the command line.

---

