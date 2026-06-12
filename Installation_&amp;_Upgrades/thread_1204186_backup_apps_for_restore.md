---
title: "backup apps for restore"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Tutigan on 2009-07-04
Hi all,

Before anyone complains, I know this has probably been covered somewhere, but I can not find it anywhere...

I dual-boot my laptop with Windoze and Ubuntu (9.04). I now want to format my lappie and use the whole hard drive for Ubuntu (I haven't used windoze in months).
I was wondering if there is a way to create a backup of all the programs I have installed and all the updates I have had to download.

---

### Post by Tutigan on 2009-07-04
bump?

---

### Post by theozzlives on 2009-07-04
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5")

---

### Post by Tutigan on 2009-07-04
That looks great, thanks for that!
But I was wondering if there is a way of backing up those packages so I don't have to re-download them... I have quite a lot installed and only a 256kbps connection...

---

### Post by ajgreeny on 2009-07-04
If all you are doing is removing windows, there is no need to re-install ubuntu.  Run your ubuntu live CD and go to *System > Administration > Partition Editor*.  In that you can just delete your windows partition and then enlarge your ubuntu partition to fill the space you have freed.  This last activity will take a long time, as in effect it is copying the partition backwards on the disk, but I have done it, so I know it can work.

Backup all your home data files first, just in case, and also just in case anything should go wrong backup the contents of /var/cache/apt/archives.  This is where all your downloaded packages are kept, so this is really the answer to your first question, but why reinstall if you don't need to?

It is just possible that the change of partitions could make the grub menu incorrect and you end up with a grub error when you boot, but we can sort that out later if needed.  Give it a try!

---

### Post by Tutigan on 2009-07-04
Thanks for your replies...
I probably should have clarified, I want to be rid of windows, and I know how to use gparted, GRUB etc, but what I want to do is a complete format of my hard drive, as my Ubuntu partition is only 20GB (of a 250GB disk) and at the end. I tried to use gparted to re-size/move it, but was unable...

---

### Post by ajgreeny on 2009-07-05
If you use the live CD you can certainly delete the windows partition(s) and then resize your ubuntu, no problem, so I repeat, why reinstall if you don't need to?  If you were trying to do this with your ubuntu install, then it is not possible, as you can't unmount the ubuntu partition.

---

### Post by Tutigan on 2009-07-05
I'm one of those people, who when re-installing, like to do so from a clean slate.
I know backing up all my apps kind of defeats that purpose, but... That's just me! I just thought that you guys would still help me anyway.

Also, it would be great to know, so I can use it at work.
(I'm 'Mr Linux' at work... we have Ubuntu loan machines that I'm constantly re-building and re-installing the same apps over and over)

---

### Post by Jesus_Valdez on 2009-07-05
Have you tried remastersys?

> What is remastersys?

* *Remastersys is a tool that can be used to do 2 things with an existing Debian,* Ubuntu or derivative installation.

It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
It can make a distributable copy you can share with friends.* This will not have any of your personal user data in it.


[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by Tutigan on 2009-07-06
Thanks Jesus_Valdez!
That looks to be exactly what I need!
Am in the progress of installing then will begin backup and re-install!

Many thanks to all those who also lent their assistance!

---

