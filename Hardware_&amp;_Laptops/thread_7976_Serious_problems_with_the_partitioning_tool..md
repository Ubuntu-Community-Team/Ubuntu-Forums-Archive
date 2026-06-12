---
title: "Serious problems with the partitioning tool."
date: 2004-12-13
forum: Hardware &amp; Laptops
---

### Post by FeliceMente on 2004-12-13
I installed Ubuntu 4.10 for the second time.
The first time using normal installation, and... I got my primary Windows XP partition totally corrupted. I thought it was grub's fault, and so I reinstalled Ubuntu, after recovering someway the lost data, this time using expert installation, so I could choose lilo.

Well... I had problems this time, too!
I lost one of the logical NTFS partitions contained in the same extended partition when Ubuntu was installed, and the previous was was corrupted (the BRs were no more correct, because two partitions overlapped). I could fortunately make everything work well again eliminating the ReiserFS and wap logical partitions I had created for Ubuntu, and manually changed the boundaries of the "corrupted" NTFS partitions using Ranish Partition Manager).

I defenitely think Ubuntu installer ha a serious problem with the partitioning tool (I've used Linux and othe OSs (even BeOS, QNX, FreeBSD, etc..) for years, without NEVER having problems with the existing partitions, and this is the first time i happens).

---

### Post by king_arthur on 2005-01-11
FeliceMente,
  
 I have recently made a couple of Warty installs on free partitions on a Win-XP system. Basically, no problem at all; actually no, I had problems when I tried "mounting" the ntfs partition during install. When the installer started complaining I forced it to go ahead but eventually, it didn't.
  
 The trick I found, was making the install without touching the Win partition and mount it later on, modifying /etc/fstab accordingly.
  
  Not easy either, to get it totally working, but finally I succeded.
  
  It is important that you actually use the mounting option **"umask** 022".
  All there is to know can be found [here]("http://linux-ntfs.sourceforge.net/").
  
  Good luck

---

