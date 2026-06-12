---
title: "UBUNTU 10.04..Less hard disk space"
date: 2010-12-29
forum: Hardware
---

### Post by rohyt on 2010-12-29
Hi..
I have installed ubuntu 10.04 inside windows in my dell vostro 1015 laptop.
The problem is it shows you have 203.5 mb space ramaining although the partition has more than 7 gb space in it..and also the computer doesnt hibernate like the windows does hibernation,,,:popcorn:

---

### Post by Sylchat on 2010-12-29
Hi,

Do you mean you have installed ubuntu on another partition, or on the same partition as windows, or inside a VirtualBox image inside Windows? 

What does give the command 'df -h' ?
The 3rd column represents the space left on various partition.

Or if you prefer graphical applications:
System > Administration > GParted (or Disk Utility)

For hibernation, you have hibernation (writes ram to HDD) or suspend (keeps only enough power to keep data in the RAM). Same difference as for [Windows]("http://pubs.logicalexpressions.com/pub0009/LPMArticle.asp?ID=745").

Syl

---

### Post by rohyt on 2010-12-30
The installation is inside windows in the same partition as the windows...But still there is more than 6-7 gb free space .still it shows there is less space....
:KS

---

### Post by mikewhatever on 2010-12-30
When installing 'inside Windows', the installation is not done to a separate partition, but to a file that resides in the Windows file system. The size of that file is allocated during the installation, and that's the size Ubuntu is allowed to use. It doesn't matter how much space there is on the partition itself.

---

### Post by rohyt on 2010-12-31
thanks mikewhatever..
I got this is exactly what happened with my laptop..CAn u suggest me how to increase the partition size for the same?????????:lolflag:

---

