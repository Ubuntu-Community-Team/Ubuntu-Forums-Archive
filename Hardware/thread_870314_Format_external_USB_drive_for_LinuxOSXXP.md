---
title: "Format external USB drive for Linux/OSX/XP"
date: 2008-07-25
forum: Hardware
---

### Post by ufugu on 2008-07-25
I'd like to format an external USB drive so that it can be moved between three different machines (a Mac, a Windows box, and an Ubuntu install).

What kind of file system will work on all three sytems?

It seemed like FAT32 would be good, but you can't exceed a file size of 4GB, so it won't work for my purposes.

I've looked around but can't find a good answer...

Thanks:)

---

### Post by ARhere on 2008-07-25
Yes you can exceed 4GB with FAT, just not with the Windows version of the format program.

Stick your USB memory into an Ubuntu machine and use GPARTED.  Format it using FAT and you are on your way.  FAT is easily supported by all OS flavors.

You could use NTFS and Ubuntu has no problem with read/write; no idea on MAC however.

-AR

---

### Post by ufugu on 2008-07-25
ARhere,

Thanks.  Your post ended up leading me to [NTFS-3G]("http://www.ntfs-3g.org/"), which should help me add NTFS support to the Mac and get to where I need to go. 

FWIW, I did try FAT earlier (drive was formatted with Gparted) and file transfers would quit with any files over the 4GB size.  Took me awhile to figure that out but then again maybe there was something else going on.  If NTFS doesn't work I'll go back to FAT and see what I can work out.

---

### Post by ARhere on 2008-07-25
4GB files?  Sheesh!!  Let me give you three options to think about...

1.  If you use FAT, it will have troubles with large files.  Formating the drive with large clusters should take care of that problem if you plan to store a LOT of large files.

2.  If you use NTFS, Windows and Ubuntu will have no problem, but Apple might depending on how good the program is.

3.  If you use EXT3, then Ubuntu will have no problems but Windows and Apple will need an additional program.  I found one easily for [Windows]("http://www.cyberciti.biz/tips/how-do-i-read-ext2-or-ext3-filesystems-under-windows-2000-or-xp-desktop.html").

This might surprise you, but I  would suggest EXT3 file system.  Why you ask???  Well for one good reason, EXT3 is _open source_.  NTFS had to be reversed engineered to get support in Linux and Mac.  EXT3 is open source so anyone can look at the code to write a good program.  This is arguable, but I think you best bet for a multi-platform file system would be the open source one.

I would love to hear a counter argument for this....
-AR

---

