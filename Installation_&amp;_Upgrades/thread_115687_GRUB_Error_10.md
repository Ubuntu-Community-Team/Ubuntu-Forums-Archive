---
title: "GRUB Error 10"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Autolycus on 2006-01-11
Howdy..

Acer, Celeron 466, 20 GB Hard drive, 192 MB RAM...

Installed Ubuntu package from CD. Erased hard drive...it automatically created: 
Partition #1 of IDE1 MAster (hda) as ext3
Partition #5 of IDE1 MAster (hda) as swap
(I have no idea what that means).

Everything installed ok as far as I could tell (Got no messages).

Removed CD from CD-ROM (as instructed); the computer rebooted....

Normal BIOS info displayed then the following was displyed on the screen:

Verifying DMI Pool Data.......
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 10


Then nothing happened, just a flashing cursor...

Help! 

I repeated the installed again with same results..

I did have to reset the BIOS so that the computer would boot from the C drive after first setting it to boot from the CD-ROM...

Again...Help!!!

TIA (Thanks in advance),

Ken

---

### Post by Maelgwyn on 2006-01-11
[quote=Autolycus]
I did have to reset the BIOS so that the computer would boot from the C drive after first setting it to boot from the CD-ROM...
[/quote]

By this, you mean you set BIOS to load from HDD rather than CD first? because there shouldn't be a C:\\ anymore. Linux doesn't use that labelling!

Grub Error 10 means that either grub is broken, or it can't find anything to load... As far as I know..

Good luck!

---

### Post by Sef on 2006-01-11
I found this on another forum:

> yerffej
10-16-2005, 03:05 AM
I had this exact problem but with a Asus motherboard. Changing the boot sequence of my two hard drives in the BIOS resolved the problem.

alainhenry
10-16-2005, 05:42 PM
I have a similar problem. Just to make sure I understand, if you change the boot order in the bios, then hda becomes hdb and conversely. You then have to update you menu.lst to take account of this, I assume ? (basically, all hd0 become hd1 and hd1 become hd0)

Link: [http://ubuntuforums.org/archive/index.php/t-75648.html]("http://ubuntuforums.org/archive/index.php/t-75648.html")

Hope this helps you

---

