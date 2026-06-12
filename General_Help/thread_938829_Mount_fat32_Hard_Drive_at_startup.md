---
title: "Mount fat32 Hard Drive at startup?"
date: 2008-10-05
forum: General Help
---

### Post by BEND IT 7 on 2008-10-05
I was wondering how I can have my fat32 hard drive that I partitioned in order to seamlessly transfer data between Ubuntu and Windows mount at startup so I can play my music (Songbird only plays the music once the drive is mounted) and transfer my files much more easily.

---

### Post by utsuprainfra on 2008-10-05
that's what /etc/fstab is for.

man fstab or look at the existing file or look for a well commented one on the net to get an idea of the syntax.

---

### Post by Nabanna on 2008-10-05
this thread will help you : [http://ubuntuforums.org/showthread.php?t=918953&highlight=Local+disc+mounting](http://ubuntuforums.org/showthread.php?t=918953&highlight=Local+disc+mounting)

---

### Post by BEND IT 7 on 2008-10-05
I'm afraid I don't understand.

I am not a big hardware guy.  Software: of course.  Anyone using Ubuntu should be a software maniac.  Hardware: I was scared to even do a basic partition using GParted.

---

### Post by Elfy on 2008-10-05
> I am not a big hardware guy. Software: of course.You should be ok then as this is software not hardware :)

Mounting a drive consists in effect of 3 parts - having somewhere to put the data (a folder), getting the software to point a partition to the folder and making sure the permissions are right.

To do the first part you need to use mkdir - decide what you want to call the mountpoint - I'll use windows. 

```
sudo mkdir /media/windows
```

Now you need to add a line to fstab, back it up first

```
sudo cp /etc/fstab /etc/fstab.0510
```

You need to know which partition you are adding to the file, run this command ```
sudo fdisk -l
```and note the number for the partition you wish to add - they will be like sda1 - change sdxy to suit below, also if you don't call the folder windows chnage that

```
gksudo gedit /etc/fstab
```

Add this line - options taken from bodhi's fstab page - referenced at the end

```
/dev/sdxy /media/windows ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

save and close gedit, now run this to make sure it has mounted

```
sudo mount -a
```

[Bodhi.zazen's fstab tome]("http://ubuntuforums.org/showthread.php?t=283131")

---

