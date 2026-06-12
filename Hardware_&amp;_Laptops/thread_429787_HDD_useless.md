---
title: "HDD useless?"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by DeadToad on 2007-05-01
On one of my computers, I had Windows 98SE on one HDD (C:\) and Ubuntu Feisty Fawn v7.04 another HDD (D:\).
I removed Feisty Fawn by using Fdisk and reformatting the HDD (D:\).
Now, I cannot access the D:\ HDD in Windows; it is not even shown in My Computer, or elsewhere.
It doesn't not exist.
When I boot up the computer with only the D:\ drive connected, it says "Grub loading.....error 17 (or similar)" and stops.
I removed the partitions and reformatted several times with Windows Fdisk, but the D:\ HDD is useless.
In Fdisk, it says under the D:\ HDD is; "Usage = 100%".

Does anyone have any suggestions?
How do I remove the Grub, so I can use this HDD again?
Thanks in advance.
:confused:

---

### Post by nystire on 2007-05-01
Try booting into windows and then shutting it down to the command prompt. Once there, run "fdisk /mbr". That should rebuild the boot record and get rid of that error message. 

After that, run fdisk and repartition the hard drive (check before saving the changes...) and then boot into window and reformat it from there. A good rule of thumb is to always use the format program for the OS that you are going to use the drive with.

---

### Post by DeadToad on 2007-05-01
nystire,
Thanks for the advice.  I forgot about MBR, but knew it was coming from there.
Been a long time since I used that command.....years.
It works fine.
Thanks a mil.
DT

---

