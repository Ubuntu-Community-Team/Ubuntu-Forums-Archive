---
title: "External hard drives"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by rayfossey on 2007-07-29
I am new to Linux... I am trying to get an external Seagate hard drive to work.... it is OK in windows... can anyone direct me to instructions on how I can get this drive to work with ubuntu  7.04....many thanks

---

### Post by moore.bryan on 2007-07-29
*how's it not working?  *

---

### Post by David A Knight on 2007-07-29
My seagate came with the drive as 1 partition formatted to ntfs, not what I wanted but it did work out the box under linux, just plug the usb cable in.

What I ended up doing was more complex as gparted cannot resize ntfs partitions.  So I formatted the partition as ext2, shrunk the partition 50%.  Then under windows as I want to use the drive there as well created a second partition and formatted it as ntfs.  The second partition had to be created under windows, vista wouldn't let me format it if the second partition was created in gparted.

Of course you may be happy with just using the whole drive as ntfs which would avoid the hoops I jumped through.

---

### Post by moore.bryan on 2007-07-29
> **David A Knight said:**
> gparted cannot resize ntfs partitions.
*gparted resized my ntfs partition... where'd you get the idea it couldn't do it?*

---

### Post by David A Knight on 2007-08-12
> **moore.bryan said:**
> *gparted resized my ntfs partition... where'd you get the idea it couldn't do it?*

From it having the option to resize disabled when I clicked on an ntfs partition.

---

### Post by moore.bryan on 2007-08-12
*did you try resizing from the ubuntu install disk or are you trying to partition before installation?*

---

### Post by David A Knight on 2007-08-12
> **moore.bryan said:**
> *did you try resizing from the ubuntu install disk or are you trying to partition before installation?*

I'm not trying anything :) I gave the steps I took to repartition my external disk, which I plug into an existing system.  Gparted in gutsy just didn't, and still doesn't give me the option to resize ntfs.

---

### Post by moore.bryan on 2007-08-12
*oh... gotcha.  i find it very strange gparted didn't work.  this may sound silly, but are you sure you unmounted the drive you were trying to resize?*

---

### Post by David A Knight on 2007-08-13
> **moore.bryan said:**
> *oh... gotcha.  i find it very strange gparted didn't work.  this may sound silly, but are you sure you unmounted the drive you were trying to resize?*

a fair question and yes, it wasn't mounted.

---

### Post by moore.bryan on 2007-08-13
*it might be worth it to try kparted...*

---

### Post by David A Knight on 2007-08-14
> **moore.bryan said:**
> *it might be worth it to try kparted...*

Well as I've been a gnome user since 0.20 then that isn't going to happen :)

---

### Post by moore.bryan on 2007-08-14
[I]:-) !!!
no worries... i'm an openbox guy who jumps between gnome/kde apps...[/I]

---

### Post by barisy on 2007-08-15
So rayfossey? Did you get your answers :) anyway i've been trying to mount my 80gig external disk to my newly installed Ubuntu 704, no success yet lol, but i think there's a chance for ppl who haven't got any data in their drives you can format it fdisk it anyway.
Nothin' is easy in this world anyhow right? :guitar:

---

