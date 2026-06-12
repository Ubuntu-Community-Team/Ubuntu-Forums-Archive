---
title: "Help"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Ptmtf on 2009-11-09
Help i just downloaded ubuntu and i installed it fine but when it said to taked cd out of the cd chamber i placed it back in for a sec. And pulled it back out and it started file checking and i pressed esc and it took me to a screen that said mount of file system failed. A maintenence shel will now be started. Control d will terminate this shell and retry. 
Root@justin-laptop:~# 
help meh does the same thing when i restart it

---

### Post by viper250 on 2009-11-09
not sure but it sounds like a corrupted install.
Try to reinstall it again. when it comes to partitioning again let it take over entire drive
it will repartition and reformat the drive. If you still have the same problem then you may need a new copy of ubuntu

---

### Post by Bucky Ball on 2009-11-09
Let it use the entire drive if you want no control whatsoever in what size your partitions are going to be or what and how many partitions you end up with. Get a pencil and paper and plan what you are going to do and go for manual partitioning. There are a lot of defaults you can set up:

/
/home
/boot
/swap

... and many others. You might want to add some of your own:

/music
/video
/data

... whatever, all depending on the size of your drive. You need these at least:

/
/home
/swap

Have any probs just ask.

* Please use descriptive thread titles in future. You will get more help that way. ;-) and welcome to the forums and Ubuntu.

---

### Post by garvinrick4 on 2009-11-09
I run the command  fsck   in terminal and it always seems
to fix itself. It will ask me to say yes to some fix's.

---

### Post by Bucky Ball on 2009-11-10
Say yes and reboot. What happens?

---

