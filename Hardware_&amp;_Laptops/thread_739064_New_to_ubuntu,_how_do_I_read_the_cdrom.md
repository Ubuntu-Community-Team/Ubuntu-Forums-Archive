---
title: "New to ubuntu, how do I read the cdrom?"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by sunny7day on 2008-03-29
Got the server version for web server. I want to install webmin but I can't connect to the internet. So I burned it to a cdrw but I don't know how to read it. And how do I copy to my local Hardrive?

---

### Post by lordatrox on 2008-03-29
I have exactly the same problem reading cd's all i get is the write image thingy, so some help would be much appreciated also by me, my dvdrom drive is a pioneer 111

---

### Post by Catalyst2Death on 2008-03-29
did you finalize the write?  did you write it in windows? I would guess that ubuntu needs the disks to be finalized in order to read the file structure, however I haven't had to deal with data cd's in ubuntu just yet...

---

### Post by oldsoundguy on 2008-03-29
and you just can't "burn the file" or copy it to a disk.  If it is an ISO you have to burn it as a data disk so that it is bootable or accessible.

For windows with Nero:
[http://wizardskeep.org/mainhall/tutor/neroiso.html](http://wizardskeep.org/mainhall/tutor/neroiso.html)

in Ubuntu:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by lordatrox on 2008-03-29
it is not writing cd's or dvd's am struggling with, its actually seeing what is on a cd or installing software from bought cd's

---

### Post by sunny7day on 2008-03-29
I did finaliz it and I choosed the ISO format in Nero.

I'm COMPLETELY new to linx, so pls i don't even know how to access the cdrom and usb drive.

It's really painful to setup a webserver on a new OS!

---

### Post by Catalyst2Death on 2008-03-29
[http://howtoforge.com/perfect_server_ubuntu7.10](http://howtoforge.com/perfect_server_ubuntu7.10)

this would be useful for setting up a web server... As for reading stuff from usb drives/ cd drives, it can be a little tricky in the beginning, but normally, and this doesn't sound like its the case, but just in case, when you put a cd in the drive, it would spin up, read the disk and then open a file browser.  At the very least, it would appear as an icon on the desktop.  You can right click, and select open.

When you plug media into the computer (cdrom or usb stick) ubuntu mounts it in /media/<type of media>

for instance, an iomega external hard drive is found under /media/iomega/

cdroms are usually

/media/cdrom<#>

usb sticks can go in as

/media/disk
/media/usb<#>

you can cd into these directories using the terminal, and then us ls to see their contents, for instance, this is what I do to navigate to my usb disk:

in the terminal:

```

$cd /media/disk/
$ls
<file 1>
<file 2
<folder 1>
<folder 2>
<file 3>
     .
     .
     .
$

```

a similar process would be used to get to a cdrom, except that sometimes it will mount to cdrom0 and other times it will be cdrom1, or just cdrom... so I usually cd into each directory, and use ls to see if there are files in that spot...

If you had an .iso image, and you thought you burned it correctly, but you actually just created a data CD with the image as a file on it, then you would not be able to see any of the files IN the iso... in order to get access them, first copy the iso to your hardisk with:

```
$cp /media/cdrom<#>/<name of iso>,iso /home/<user>/Desktop/
```

(you can mount it from the disk, but you'll get better performance if you copy it to the harddrive first...)

then you need to create a place to mount the disk:

```
$sudo mkdir /media/<name of place to mount>
```

ok, now were ready to mount the iso:

```
$sudo mount /home/<user>/Desktop/<name of iso>.iso /media/<name of place to mount>/ -t iso9660 -o loop
```

now, you should see a disk icon on your desktop named <name of place to mount> which you can interact with as though it were a real disk!

when your all done you can use 

```
$sudo umount /media/<name of iso>
$sudo rm -rv /media/<name of iso>
```

if your uncomfortable using rm -rv ( I wasn't for a while when I first started), you don't need to do it, it just deletes the folder and keeps the media folder clean and tidy.

if you don't like the command line approach, this guide:
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

will walk you through setting up a nautilus script for doing this job.

---

### Post by sunny7day on 2008-03-29
$cd /media/disk/
$ls

this trick won't work for me, the cdrom drive don't even spin up. The media folder listed cdrom and cdrom0, i tried both.

---

### Post by Catalyst2Death on 2008-03-29
have you tried other cd media (ie the original ubuntu cdrom?)  I would try to do the same thing with a cd you know you can read from both windows and ubuntu, a cd that you purchased would be great!  Try the above again, this will tell you if its the hardware or the disk itself which is at fault. 

 If its hardware, its out of my depth, I've never had to deal with cd drives acting up, so I can't be of much help.  If its the media, (the disk you burned) then there are things that you can try to get it to burn correctly.

---

