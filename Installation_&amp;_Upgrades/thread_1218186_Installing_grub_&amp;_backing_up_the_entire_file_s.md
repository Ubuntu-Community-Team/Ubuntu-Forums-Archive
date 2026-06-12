---
title: "Installing grub &amp; backing up the entire file system"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by 05bit044 on 2009-07-20
hi
I have  dell xps studio with 320 hard disk which contains a recovery partion for windows vista. I installed ubuntu 9.04 in the last 30 gb of my hard disk

1) I may have to re-install windows vista using my recovery which may delete the grub. After the re-installation of vista, i need to install the grub again so that i can choose the operating system. can anyone tel me how to install the grub again. 

2)After installing ubuntu, i spent a lot of time installing large number of application packages. If i have to re-install ubuntu again, i wont have patience to install all those applications once more. Is there any method or procedure to back up my entire filesystem as an image so that i can restore it back. If the methodology exists, can anyone tel me how to back up the filesystem and how to restore it.

---

### Post by dstew on 2009-07-20
You can use Partimage to make an image of your Ubuntu partition. See [this How-To]("http://www.psychocats.net/ubuntu/partimage").

To restore grub, see [this How-To]("http://ubuntuforums.org/showthread.php?t=224351"). If you don't change your partition structure, just re-install Vista and Ubuntu, this should work. If you re-arrange your partitions, you many have to edit the grub menu.lst file.

---

### Post by jayanramesh on 2009-09-22
You can't use partimage if your file system is ext4 for it won't support.Instead you had better go for FSarchiver if your filesystem is ext4.

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

---

### Post by raymondh on 2009-09-22
I have used [aptonCD]("http://aptoncd.sourceforge.net/") with success.... transferring from same versions.

Aside from my regular rsync (to back-up), I also use [PING]("http://ping.windowsdream.com/") to create an image of my partitions (or HD) and back it up externally.  Have not gotten to resort to it though ;)

Good luck

---

