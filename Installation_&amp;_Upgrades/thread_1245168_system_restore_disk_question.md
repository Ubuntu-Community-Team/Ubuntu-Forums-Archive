---
title: "system restore disk question"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by baconbuttyman on 2009-08-20
My ability with pcs is quite advanced, BUT, i am not an advanced linux user, quite the oposit, ihave no knowlege of programming etc but i really like Ubuntu, i now have it running how i like it, but its taken a while of tweeking and referencing from the vast help on the net, is there a program to make a system restore disk with all my settings and emails settings etc, i would like to write it to a dvd.

---

### Post by dstew on 2009-08-20
There are several ways to do this. It sounds like you want to create some kind of system archive. You can do this by archiving files, or by creating images of your partitions. See [this How-To]("https://help.ubuntu.com/community/BackupYourSystem") for more information.

There is a program, [sbackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"), that creates archives using a graphical interface that is popular. I read a post somewhere that it had problems with a file system called gvfs, but if you have the usual ext3 or ext4, it is probably OK to use sbackup.

---

### Post by baconbuttyman on 2009-08-26
i think you mis understand me, please use plain englesh when replying as i do not have a clue what you are talking about with linux systems, i am very new and learning as i go..slowly lol.
what i mean, is create a system restore disc so if ubuntu cocks up and i have to reinstall the system all i need to do is pop the restore disk in and it restores everything, from my emails to the wallpaper, i dont know where the installation files are kept or such

---

### Post by SlugSlug on 2009-08-26
search for simple backup in add / remove programs

---

### Post by dstew on 2009-08-26
If you really want a complete restoration, including programs and data, you should make an image of the root partition or the disk. Two programs that do this are [partimage]("http://www.partimage.org/Main_Page") and [clonezilla]("http://clonezilla.org/"). I have never used them, so you will have to read the web pages to figure out how to do it. You can probably install the programs using Synaptic. You might need to enable the universe repository (System --> Administration --> Software Sources).

---

### Post by oldos2er on 2009-08-29
> **baconbuttyman said:**
>  what i mean, is create a system restore disc so if ubuntu cocks up and i have to reinstall the system all i need to do is pop the restore disk in and it restores everything, from my emails to the wallpaper, i dont know where the installation files are kept or such

 You might want to look here: [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by raymondh on 2009-08-29
I use a 2-pronged approach:

rsync to back-up my data (actually using a frontend program, GUI-based,  called [grsync]("http://allmyapps.com/app/ubuntu-9.04/grsync") .... found in synaptic)...... and 

[PING]("http://ping.windowsdream.com/") to create an image of my HD and partitions.

Grsync is done every week whilst PING is about 1x a month and stored in an external HD.

Good luck and happy ubuntu-ing.

---

