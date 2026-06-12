---
title: "Adding new hard drive problem."
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by SteffJay on 2006-10-21
Here is the problem....  After reading most of the threads here concerning adding a vfat 80Gb HDD to my Ubuntu 6.06 D/D system, it can still not be recognised by the system or be accessed by anybody even root. [IMG]http://www.steffsoft.com/pic1.jpg[/IMG]

Can anyone please explain how i can achieve this ??

---

### Post by lloyd_b on 2006-10-21
The command you're looking for is:

```
sudo mount /dev/hdc5 /work
```

You have to tell it what to mount first, then tell it where to mount it.

Note:  It may require you to specify the filesystem type as well.  If that command fails, then try:

```
sudo mount -t vfat /dev/hdc5 /work
```

To have it automagically mount on startup, you'll need to edit the "/etc/fstab" file.

Lloyd B.

---

### Post by SteffJay on 2006-10-22
Hello **lloyd_b**. Thanks for the reply. Having tried the commands you have given me, it still refuses to mount or even find the new drive:

[b]root@server:~# sudo mount /dev/hdc5 /Work
mount: mount point /Work does not exist
root@server:~# sudo mount -t vfat /dev/hdc5 /Work
mount: mount point /Work does not exist
root@server:~#[/b]

Still cannot figure this out.  ](*,)

---

### Post by SteffJay on 2006-10-22
*******************
Update
*******************

It seems that the vfat drive need to be formated to the path that the system requires, so if the drive is called Work and i would like to use the drive apart from root, i need to format it as **/home/Work** as vfat then i can mount it using the commands that **lloyd_b** has given. After it has mounted, it needs to be write enabled by myself as well as root: **chmod 775 -R /home/Work**. Still don't know why this should be but it is available now. ;)

---

### Post by iLoVe.cF- on 2006-10-22
uhm.. since this post is made..

How do u get a ext3 partition to be read---write ?

I can only get read access.. 

YEs im a linux noob.. 2nd week with linux, 13 of the days.. went to trying to install intel video card shit, gave up, got me some new parts for desktop comp, ati.. almost fine :D

but got like 1600 gb i wanna use.. 
Using like 200 now :'(

---

### Post by SteffJay on 2006-10-22
Hello **iLoVe.cF-**. I'm not quite sure about ext3 partitions... I had a spare 80Gb drive available that was already formated to vfat (FAT32). If the drive is visible on your system (i take it it is as you can only read from it), you only need to **sudo chmod 775 -R /***** what ever its is called and i would think that will make it read/write available. No doubt if i'm wrong, some kind sole will put us both right.....  ;)

---

### Post by Kulgan on 2006-10-22
All I have done is stuff to do with usb drives - [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) was a great help. It gives the basics of media mounting in linux...

---

### Post by SC_Frank on 2006-11-03
iLoVe.cF-

I've tried to find a way to do this in the file manager and here's what I did (assuming the drive is mounted)
sudo Nautilus, find drive and right click on it. Set permissions for read/write and ownership. The next time you open up nautilus, or any other file manager, you should be able to read/write to the mount volume. It's worked fine for me ---8) 

Hope this helps -

---

### Post by andradelipe on 2006-11-03
> **SteffJay said:**
> Hello **lloyd_b**. Thanks for the reply. Having tried the commands you have given me, it still refuses to mount or even find the new drive:

[b]root@server:~# sudo mount /dev/hdc5 /Work
mount: mount point /Work does not exist
root@server:~# sudo mount -t vfat /dev/hdc5 /Work
mount: mount point /Work does not exist
root@server:~#[/b]

Still cannot figure this out.  ](*,)

Man, first of all, you need to create this directory!

```
mkdir /Work
```

and after that, use:

```
mount -t vfat /dev/hdc5 /work
```

Why r u root?

---

### Post by Kulgan on 2006-11-03
> Why r u root?

cause he has to be... That's the problem - the inability to mount without being root. 

I would still reccommend [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) as the best solution...

---

