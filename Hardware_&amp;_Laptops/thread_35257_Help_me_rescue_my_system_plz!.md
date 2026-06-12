---
title: "Help me rescue my system plz!"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by void_false on 2005-05-18
Hello people!

One one forum i've read a tip about how can I increase speed of my HD. The command was 
```
hdparm -m2c3u1d1k1K1 -X69 /dev/hda
``` 

After that my file system just crashed and Ubuntu doesnt boot anymore.
SoI took my Knoppix CD and ran fsck. It found many errors and fixed them (?)

That didnt help. First I thought my system was empty. There was only one folder - lost+found. When I entered the folder I saw there many files and folders with names like #328321 
So i ran df -h and discovered that my linux partition has 3.2GB of used space!! 
I think that all those weird files/folders are my beloved Ubuntu. Is there any way to rescue it?
TIA!

---

### Post by void_false on 2005-05-18
I was examining all those weird folders and found out that it is actually my system files.  ;-) 
I've already found /mnt /etc /home /dev
All files seem to be OK.
Now how can I put all this mess into right place?

---

### Post by void_false on 2005-05-18
Sorry for my impatience but plz plz plz help me. :-|  ](*,)

---

### Post by nocturn on 2005-05-18
The bad news is that there is no quick recovery out of this... I might even suggest saving your data and reinstalling.

If you do want to recover,you need to find every directory and put it in its place, there is no automation or help for this.

If you are in this state, things must have gone really wrong, I have never heard of this happening.

---

### Post by void_false on 2005-05-18
OK guys. I've restored dev, home, mnt and etc by myself. Now I need a little help from you. I've made a screenshots of files and folders that I dont know where they supposed to be.

[[img=http://img277.echo.cx/img277/992/s13ml.th.jpg]](http://img277.echo.cx/my.php?image=s13ml.jpg)
[[img=http://img136.echo.cx/img136/2164/s26qc.th.jpg]](http://img136.echo.cx/my.php?image=s26qc.jpg)
[[img=http://img136.echo.cx/img136/6916/s32yt.th.jpg]](http://img136.echo.cx/my.php?image=s32yt.jpg)
[[img=http://img136.echo.cx/img136/1027/s40ft.th.jpg]](http://img136.echo.cx/my.php?image=s40ft.jpg)
[[img=http://img136.echo.cx/img136/2830/s52rz.th.jpg]](http://img136.echo.cx/my.php?image=s52rz.jpg) 
[[img=http://img174.echo.cx/img174/9186/s66ie.th.jpg]](http://img174.echo.cx/my.php?image=s66ie.jpg)
[[img=http://img174.echo.cx/img174/198/s74vw.th.jpg]](http://img174.echo.cx/my.php?image=s74vw.jpg)
[[img=http://img174.echo.cx/img174/5526/s95ye.th.jpg]](http://img174.echo.cx/my.php?image=s95ye.jpg)

These supposed to be symlinks. What are their original names?

[[img=http://img174.echo.cx/img174/6830/s109bl.th.jpg]](http://img174.echo.cx/my.php?image=s109bl.jpg)

TIA!

---

