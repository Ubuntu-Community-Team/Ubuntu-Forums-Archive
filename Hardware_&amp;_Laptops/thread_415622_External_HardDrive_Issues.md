---
title: "External HardDrive Issues"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by jmemm37 on 2007-04-20
I purchased a Maxtor One Touch 3 Mini Edition external hard drive to be used in conjuntion with my laptop and Ubuntu. The problem I am having is that Ubuntu is reading it only as a read only drive which prevents me from changing its permissions. I do want the capacity to write to the drive so I can store my music files on it (mp3 form) so I can also share it with my wife's windows desktop. Can anyone help me with this?

---

### Post by tmatt95 on 2007-04-20
> **jmemm37 said:**
> I purchased a Maxtor One Touch 3 Mini Edition external hard drive to be used in conjuntion with my laptop and Ubuntu. The problem I am having is that Ubuntu is reading it only as a read only drive which prevents me from changing its permissions. I do want the capacity to write to the drive so I can store my music files on it (mp3 form) so I can also share it with my wife's windows desktop. Can anyone help me with this?
The drive needs to be formated in a way that it can be read/ written to by Linux. I used a special program :
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
to format the drive to FAT32, when I got my USB drive and it works fine for me and can still be read by windows if needed.Hope this helps,
Best regards,
Matt

---

