---
title: "Usb portable hard drive"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by t3roriz3r on 2007-05-03
Hi, was just wonderin if an usb external drive will be recognised and run automatically it ubuntu? In college at the moment and just wondering, only got it installed last nite and was just thinking bout connecting it to transfer some music. Will the music transfer ok?

I know the best answer is prob to try it but im just wondering.

Thanks

---

### Post by jjordan on 2007-05-03
The short answer is yes it will work, I use several external drives with several different Linux based systems.

Now for the long answer.  If the external HD is formated with Fat32 you will have no difficulty reading and writing under Windows, Linux or MAC.  There are other considerations, reliability, security, the 2GB/file limit for example.  If the drive is formated with NTFS (Windows NT/XP/Vista) take a look at NTFS-3g to be able to read and write to the drive.  NTFS-3g is included with Fiesty (7.04) but not installed by default (it might be if you have any NTFS drives installed when you do the installation).  I have a couple of MACs but have not really tried to access HFS formated external drives, there are tools included in Fiesty to do so. 

-j

---

### Post by t3roriz3r on 2007-05-03
Thanks ill have to try it out

---

