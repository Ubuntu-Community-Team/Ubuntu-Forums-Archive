---
title: "Xubuntu Feisty: 1 Zip Disk 4 Zip Icons on Desktop"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by xerman on 2007-04-20
Hello there,

I've just installed Xubuntu on an oldie:

Pentium 200MMX
160MB ram
13GB HD
4mb vram Matrox Millenium
20x CD
8x/4x/32x CDRW

I try to use an not so old external zip drive (USB), and when i put a Zip drive into the ZipUnit on the Xubuntu Desktop appear 4 Zip Icons:
 3 icons named "Zip Drive"
 1 Icon named "Name" (the name of the drive)

The "Zip Drive" Icons produce Unknown Error when trying to mount or open. There is no way to unmount them nor erase them.

Any help on how to get rid of those extra icons will be appreciated. I presume I will never put 2 zip disks into the drive... that way I would have 8 zip icons, and a "Guinness World of Records" Zip Drive capable of reading 2 disks, or most probably, a Zip of Junk.

Thanks a Lot.
Xermán

---

### Post by xerman on 2007-04-24
Hello there:

For those who have this issue too, I found out what was the problem:

The Zip Disks I was using were MacOS formatted, and Formating a disk in macos with macos filesystem creates 4 partitions on the disk, 3 and the 4th which is the one that handles the data.

Formatting the Zip Disk in Linux removing all partitions solved the issue. 

But THERE SHOULD BE an EASY way to format a Zip Drive, like "Right Click on the disk and select a Format Option". I had to erase it in Gparted.

Take care.
Xermán

---

