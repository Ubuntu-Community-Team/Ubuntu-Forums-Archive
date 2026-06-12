---
title: "Clone a Hard Drive."
date: 2014-05-18
forum: Hardware
---

### Post by mebofume on 2014-05-18
I purchased a HP hard drive and I really wished I hadn't. I got a SSD, but all the Windows Cloning Software is not working. No matter what I do I can't get it to clone windows files. So I turned to Ubuntu. Unfortunately after 6 hours of trolling Google, I have had to come here. I downloaded a few pieces of Software, but they not showing in Ubuntu IE partclone. Just can't find it, in Software it says Installed, but can;t find it. So really annoying. I don't want to use dd, 1 its confusing, 2 everywhere says 1 mistake and its game over. So I need a genuine clone software, that is easy to use and doesn't hide. Really stressed I thought Disk cloning was simple. it used to be, but Microsoft have made it so much hardwork. Clonezilla doesn;t seem to exist, Partclone hides. So any genuine working clone program perferablely in software down loads built into Ubuntu. Search is confusing and DD is a no no Not that its in Software anyway. Please help

---

### Post by oldfred on 2014-05-18
Are you keeping old drive installed?
If you you may have issues. Partitions will have same UUIDs and then system gets confused on which is correct.

This is more for backup and restore to same drive.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

For Linux these are often suggested.

 [http://clonezilla.org/](http://clonezilla.org/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by mastablasta on 2014-05-19
you can use redobackup (it uses a graphical frontend for partclone) and cloning can't get simpler than that. good luck...: 
[http://redobackup.org/](http://redobackup.org/)
clonezilla is another good option, but it is for more advanced users than knwo exactly what they want as it offers many settings.: [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by mebofume on 2014-05-19
Cheers for the reply, Clonezilla is not available, no where has a genuine download. I will try redobackup, But I did try last night with no luck.

Basically, I want to do clone/mirror copy of the HD onto a SSD, but its more trouble than its worth.

---

### Post by mastablasta on 2014-05-19
what do you mean? clonezilla downloads: [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

redobackup needs to be downloaded and then you create live CD/USD and boot from it (select it as boot device). once it starts up follow the instructions and select what you want to clone Disk & partitions (by default the whole disk will be selected). and then you select where you want to create the image (drive&folder). and then you restore the image (to a different drive).

---

### Post by mastablasta on 2014-05-19
ah direct device to device cloning with Clonezilla - [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by Mark Phelps on 2014-05-20
Don't know about Windows cloning software NOT working -- as I have used Macrium Reflect to clone disks several times and have have no problems with it whatsoever.

---

### Post by psfal on 2014-11-09
> **mastablasta said:**
> ah direct device to device cloning with Clonezilla - [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

Thanks for this, just what I was searching for, I'm glad someone else already asked and the answer was waiting for me :)

---

