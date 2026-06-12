---
title: "Help with Partition"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by Yes_It's_Me on 2006-02-02
Hi, I just put win xp and ubuntu on my new comp in duel boot, i created a partition (Fat32) as a shared partition so that both OS's could read and write to, however, when i go into windows it is under my computer and everything seems fine, but under ubuntu in computer it has nothing but the OS's partition and that sort of stuff, how do i get it to work as a shared drive in ubuntu?

---

### Post by krusbjorn on 2006-02-02
You need to mount it manually, using the "mount /dev/hda1 /<where to mount it>" (replace "hda1" with the actual name of your FAT32 partition.)

However, you might want to check the link below out. It's a piece of software that lets your Windows OS read your linux file system (ext2 and ext3). Meaning you can access your Ubuntu partition from Windows.

_[http://www.fs-driver.org/](http://www.fs-driver.org/)_[]("http://e2fsprogs.sourceforge.net/ext2.html")

---

### Post by Yes_It's_Me on 2006-02-02
The name of the partition is sda5, so do i type in "mount /dev/sda5", is that all?

---

### Post by Sutekh on 2006-02-02
I would use this entry in my fstab to make it permanent.
```
/dev/sda5  **/media/shared**  vfat  rw,users,gid=users,umask=000,  0  0
```
I would just change the mount point (bold) to where you would like to mount the FAT32partition.

Edit; Here's a good link for explaining it all

[Ubuntu Wiki - Mounting Windows Partitions]("https://wiki.ubuntu.com/MountingWindowsPartitions")

It has commands for one-time mountings and entries for permanent mounting.

---

### Post by Yes_It's_Me on 2006-02-03
Do i just paste that on the end of the file?, when i try to do that it deosn't let me (it deosn't let me type in the file)

---

### Post by Sutekh on 2006-02-03
[QUOTE=Yes_It's_Me]Do i just paste that on the end of the file?, when i try to do that it deosn't let me (it deosn't let me type in the file)[/QUOTE]
Begging my pardon, I assumed too much.

To edit your fstab (if you want the permanent mount option), you'll need to do so with sudo

Because its always a good idea to backup important files before editing
```
sudo cp /etc/fstab /etc/fstab_bak
```

To edit the file you'll need
```

sudo gedit /etc/fstab 
```

---

### Post by Yes_It's_Me on 2006-02-03
Yay, thanks i can now edit it, so do i just paste it on the end?
Sorry if these are incredibly n00bish questions.

---

### Post by Sutekh on 2006-02-03
[QUOTE=Yes_It's_Me]Yay, thanks i can now edit it, so do i just paste it on the end?[/QUOTE]
I would paste it in order numerically so after sda4 or whatever.  It makes it easier if you ever look at /etc/fstab again.

[QUOTE=Yes_It's_Me]
Sorry if these are incredibly n00bish questions.[/QUOTE]
No need to apologise!  Gotta start somewhere, keep at it!

---

### Post by Yes_It's_Me on 2006-02-03
Ok, getting ever so much closer now, i edited that file and all and reseted my computer (guessed it was logical), and while it was starting up i saw it say something along the lines of "mounting local drives, failed", i only caught it for a second. When it finished starting up i went to "computer" and there is a drive called shared thare but when i click on it it says "unable to mount the selected volume, mount: mount point /media/shared does not exist", and it is right because when i go to the directory it is not there. What is the next step?

---

### Post by Sutekh on 2006-02-03
[QUOTE=Yes_It's_Me]Ok, getting ever so much closer now, i edited that file and all and reseted my computer (guessed it was logical), and while it was starting up i saw it say something along the lines of "mounting local drives, failed", i only caught it for a second. When it finished starting up i went to "computer" and there is a drive called shared thare but when i click on it it says "unable to mount the selected volume, mount: mount point /media/shared does not exist", and it is right because when i go to the directory it is not there. What is the next step?[/QUOTE]
Yep that's my fault.  There needs to be a folder for the mount point to go to.  So you need to create the folder where you want the FAT32 partition to be mounted to.  /media/shared was just from my setup, you can have whatever you like.

To create the folder you should use
```

mkdir /media/shared
```
you can change /media/shared to whatever you like, just make sure that the entry in /etc/fstab is the same as the folder you make with the mkdir command.

Also to save you time (again I should have said this earlier), you can apply the new mount options by using
```
sudo mount -a
```
Now you don't have to restart

---

### Post by Yes_It's_Me on 2006-02-03
YAY! it works! For some reason in the shared folder there is 2 more folders "recycled" and"system volume information", is it safe to delete these? thanks for all your help

---

### Post by Sutekh on 2006-02-03
I wouldn't delete them, Windows puts them in, when you use the folder in windows.  It might be okay, but I'd leave em just in case.

No probs glad its working.

---

### Post by Yes_It's_Me on 2006-02-03
Ok i will leave them, thanks for all the help

---

### Post by pedwards on 2006-02-03
hey i have followed all you steps but now i have only read permissions on my fat,
and i am unable to read or write to the windows fs that i mounted


any help here?

---

### Post by Sutekh on 2006-02-03
Could you post the line you used to mount the FAT partition?

---

