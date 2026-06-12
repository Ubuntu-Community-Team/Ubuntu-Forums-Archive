---
title: "Looking for Ubuntu Backup"
date: 2008-11-06
forum: General Help
---

### Post by shortcut144 on 2008-11-06
Looking for a program that will allow me to backup my Ubuntu (I use Xubuntu if that matters).  I want to be able to recover easily if I was ever to get a huge crash.

I any tips or links from anyone?

---

### Post by Idefix82 on 2008-11-06
You don't need any dedicated software (although there is some around). To backup your entire system or only some folders is one line in the terminal. Have a look at this very nice howto: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by Cl0ud9 on 2008-11-06
I you are looking to keep all of your files in /home secure if something drastic happens to your (X)ubuntu install, I would recommend mounting /home to its own partition.

---

### Post by shortcut144 on 2008-11-06
Both ideas are really good.  I have no idea how to mount my Home folder on to its own partition.

---

### Post by DGortze380 on 2008-11-06
man rsync

---

### Post by xak on 2008-11-06
> **Idefix82 said:**
> Have a look at this very nice howto: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

...which, magically, is the first Google result for 'ubuntu backup' :mrgreen:

On a more serious note, I vouch for using this method and using it to actually recover and has always been completely successful.

---

### Post by scouser73 on 2008-11-06
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by jimv on 2008-11-06
PartImage is a pretty good option.  It makes an image of your Ubuntu partition, which you can later restore if something goes wrong.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

---

