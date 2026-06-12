---
title: "Grub problems with 3rd Hard Drive"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by chilisastry on 2007-10-11
My computer has three drives: a SCSI drive, and two IDE drives.  Windows 2000 is installed on the SCSI drive.  Feisty Fawn is installed on a partition on the first IDE (Master) drive, Grub is also on this drive in a separate boot partition.  At the time of installing Feisty, only these two drives were present, and I could startup in either Windows or Ubunto without any problems.  At that time, the BIOS numbered the drives as:
Master IDE     hd0
SCSI               hd1

Subsequently, I added a Slave IDE drive.  The BIOS now numbers the drives as:
Master IDE    hd0
Slave IDE      hd1
SCSI             hd2

I can now boot up in Ubuntu, but not in Windows anymore.

I edited /boot/grub/menu.lst and change the 'root' directive from hd1 to hd2.

_Before:_
title                          Microsoft Windows 2000 Server
root                         (hd1,0)
savedefault
makeactive
map                         (hd0)  (hd1)
map                         (hd1)  (hd0)
chainloader              +1

_After:_
title                          Microsoft Windows 2000 Server
root                         (hd2,0)
savedefault
makeactive
map                         (hd0)  (hd1)
map                         (hd1)  (hd0)
chainloader              +1

No dice!

I shouldn't have to reinstall Feisty Fawn to get this to work!

---

### Post by dabl on 2007-10-11
Maybe ...

> After:
title Microsoft Windows 2000 Server
root (hd2,0)
savedefault
makeactive
map (hd0) (hd**2**)
map (hd**2**) (hd0)
chainloader +1

:)

---

### Post by chilisastry on 2007-10-12
It worked.  Thank you.  I thought I had tried it severa ldays ago, but perhaps I did not.

---

