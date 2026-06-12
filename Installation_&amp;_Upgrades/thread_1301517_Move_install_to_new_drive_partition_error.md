---
title: "Move install to new drive partition error"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by carpman on 2009-10-26
Hello, ok need to move a ubunto install to a new drive partition. Old drive had windows also installed but new drive will just have ubuntu.


I tried cloning partition to partition with number of app but all failed, even if they did clone i kept getting file errors on lost&found folder that prevented booting, even tried deleting this folder but could not?


Have created new partition and swap file on new drive and installed grub and tried just moving data over

cp -R

this moved install fine and could run fsck on lost&found folder, still can't delete contents, but there are file permission errors?

IE login won't recognise passwords, starting X from console etc

So question is can i do a quick change of permissions and if so on what files/dir ?

If not what is best command to copy over old install to new drive partition?

many thanks

---

### Post by louieb on 2009-10-26
I've used Gparted in the past to copy the Ubuntu install from one drive to another. 
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

another option of cp is -a (it preserves permissions)

---

