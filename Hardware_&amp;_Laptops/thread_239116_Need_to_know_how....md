---
title: "Need to know how..."
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by Jan Scheffer on 2006-08-18
English.
Hello,

Maybe theres someone who knows how to make my old windows partitions Like my external disk (USB) not only readable but fully accessed?

And how to make all the NTFS internal disks accesseble in Ubuntu?

Iam a newbee in linux id liked to instal and use ubuntu a lot but i dont know how to do this all

Iam dutch maybe there is someone who can help me in dutch?

Nederlands.
Hallo mischien is er iemand die me kan helpen mijn externe schijf (USB) behalve alleen readable maar compleet accesseble?

En hoe ik mn NTFS schijven kan benaderen in Ubuntu?

Ik ben nieuw met Ubuntu heb al van alles geprobeert te instaleren maar dit is de eerste distributie die ik draaiend krijg en werkend op internet

Is er iemand die me met deze "problemen" kan helpen???


Jan Scheffer

---

### Post by Sef on 2006-08-19
> And how to make all the NTFS internal disks accesseble in Ubuntu?

Linux can read, but not write to NTFS.  To be able to share files with Windows, you need to create an ext2 or fat32 file.

Read this on [how to dual boot]("http://users.bigpond.net.au/hermanzone/"), so you can understand how set up a shared partition.  Note: you do not need to reinstall the operating system if you have dual booted alread.  Just need some free space on your hard disk to set up your partition.  If that is the case, then I would use [GParted]("http://gparted.sourceforge.net/livecd.php")to install the new partition.

---

