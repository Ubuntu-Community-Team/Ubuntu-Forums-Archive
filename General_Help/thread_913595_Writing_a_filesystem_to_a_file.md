---
title: "Writing a filesystem to a file"
date: 2008-09-07
forum: General Help
---

### Post by Mr.Macdonald on 2008-09-07
Using the dd command i have successfully written the contents of a hard disk to a file, and then mounted it. The problem is that the size of the mounted disk-file is the same as that of the hard disk. Can i use dd to make a disk image without a disk existing, and choose the size?

---

### Post by unutbu on 2008-09-07
If what you are trying to do is do a dd-style backup of a partition but without copying empty space, then I think Partimage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)) may be the solution. There is also a howto guide here: [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522).

If, on the other hand, you want to create a filesystem in a file (rather than a partition) and you want the file to be of a fixed size, then I'm not sure. I suspect there is a way, but I'd have to do some searching.

---

