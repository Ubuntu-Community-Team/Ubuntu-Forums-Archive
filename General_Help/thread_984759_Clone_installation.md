---
title: "Clone installation"
date: 2008-11-16
forum: General Help
---

### Post by transmition on 2008-11-16
I have begun to run out of space on my macbook 4,1 and have decided that I want to resize my partition. To my knowledge, the only way to do this is to back up my installation and then repartition my disk. 

If I were to clone my installation (which would include all of my programs, settings, and themes) Would all I have to do is backup the following directories and paste them over to the fresh install?

/etc
/home
/usr
/var 

Thank you.

---

### Post by Partyboi2 on 2008-11-18
Have you considered using gparted to resize your partitions? Boot a ubuntu live cd and open gparted (System>Admin>Partition Editor) then unmount the partitions and use the resize tool to make the changes.

---

### Post by dcstar on 2008-11-18
> **Partyboi2 said:**
> Have you considered using gparted to resize your partitions? Boot a ubuntu live cd and open gparted (System>Admin>Partition Editor) then unmount the partitions and use the resize tool to make the changes.

And if you are gojng to that amount of trouble, you should also set up a separate /home partition.

---

### Post by scouser73 on 2008-11-18
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by transmition on 2008-11-18
Are you sure Gparted can resize an HFS file system (that of the Mac) 

As well, would copying the contents of the folders
/etc
/home
/usr
/var 
back up all of my prefrences? I am running Ibex, and I believe I am running the AMD 64 version of Ubuntu, when I have found out that I should be running the 32 bit version for intel computers. I think this fresh install would also speed things up anyway.

---

### Post by Keen101 on 2008-11-18
I don't think gparted can resize HFS partitions. But, you could back up your data and then create a bigger HFS partition with gparted. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Partyboi2 on 2008-11-18
My mistake you are correct gparted cannot resize hfs, but I have read that parted could possibly resize hfs.
On the mac installation disc,  can't you use Disk Utility's partitioning feature to resize the volume without wiping it?

---

### Post by transmition on 2008-11-18
I do not believe so, I recall reading a forum about boot camp and windows, and the only way to resize the partition was to back up your windows install, remove your partition, create a new larger partition, and then reinstall your backup of windows.

Sorry if I seem a bit naggy with this question, but if I back up /etc /home /usr and /var, will this let back up all of my themes/prefrences?

---

### Post by Keen101 on 2008-11-19
> Sorry if I seem a bit naggy with this question, but if I back up /etc /home /usr and /var, will this let back up all of my themes/prefrences?

It should. Just don't forget the hidden files. Try looking at other backup threads to make sure your not forgetting a folder.

---

### Post by nixscripter on 2008-11-25
Having played with Linux on a Mac, I would simply answer the question about repartitioning.

gparted **can** change the size of HFS+ partitions, but it can only make them **smaller**. Strange, eh? You might be able to juggle the data or something using this if you are clever.

Disk Utility can't change the size of an existing partition at all, only wipe it and create the new one.

---

### Post by transmition on 2008-11-25
Thanks, but I took the cheap way out. I wrote down my programs, copied over data like music files, and then just did a fresh install using settings from memory. I appreciate all the advice and knowledge I gained from this post however.

---

