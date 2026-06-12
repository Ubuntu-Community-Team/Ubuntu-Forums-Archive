---
title: "Wipe it clean"
date: 2008-08-12
forum: Hardware
---

### Post by Just-trevor on 2008-08-12
Is there a way to wipe a hard drive clean, and just start over?

I have windows installed, but it isn't registered and I don't have the means to register it and it is wasting hard drive space and I can't remove it.

I've thought it through, and there is nothing I really need to keep on this computer and i can replace everything I do need in a few hours, maybe less.

So how do I just wipe it clean? 

Do magnets work?

---

### Post by LuserName on 2008-08-12
Why can't you just reformat it?

---

### Post by tamoneya on 2008-08-12
just write over it with a new partition.  launch ubuntu and run gparted:```
sudo apt-get install gparted
gksudo gparted
```

Then just right click on windows and select delete.  Then in the empty space you can make a new partition (format as ext3).  Then mount it.

---

### Post by tuxxy on 2008-08-12
lol at magnets, run the program **gparted** from the live CD before you install Ubuntu, wipe the windows partition using the app and install Ubuntu fresh on its own drive :)

---

### Post by Just-trevor on 2008-08-12
now what...

How do I reformat it?

---

### Post by tamoneya on 2008-08-13
> **Just-trevor said:**
> now what...

How do I reformat it?

right click on the one labeled sda1.  Then select delete.  That removes windows.  Then right click where that used to be and select new partition.  When it asks you for the format you should select ext3.

---

### Post by cdaringe on 2008-08-13
right.

when everything is deleted, it should say unused or "unallocated space."  Selecting to format all of the unallocated space as ext3 is reformatting the drive to ubuntu's filesystem.  what it may not say is that all gnu/linux distributions (such as ubuntu) also have another partition that is more or less for buffering data, called a swap partition.  if you've installed ubuntu before, and partitioned the drives manually, you will have run into this (otherwise, it automatically actually creates TWO partitions when installing ubuntu).  you should create a "swap" partition as well (500 mb to 2000 mb, depending on your drive size. ps, those numbers may be a bit willy nilly.  anything over 500 mb on a new machine is probably fine).

if this is all too much info, let us know.  if you are looking for a quick and easy method to reinstall your OS, the best advice is one of these:
1) if you are going to install ubuntu, just boot the ubuntu live CD, double click install, and when it comes to the hard drive screen, select the "use entire disk" option (there are only 3 or for options on that screen), and it will automate all of this for you :)

2) if you are going back to windoze, boot from the windows CD, and there should be an install windows option.  there is an option to reformat the drive before reinstallation.  you can probably handle it from there

hope that helps :)

---

### Post by sandysandy on 2008-08-13
look here also

[http://sourceforge.net/projects/dban/](http://sourceforge.net/projects/dban/)

[http://www.dban.org/](http://www.dban.org/)

regards

---

### Post by Just-trevor on 2008-08-13
ok, I don't have a floppy drive, or a usb flash drive, so dban is out:(

Once i get my hands on a blank disk, I'll just do the "use all disk space" option, then I'll finally have more than 22 gigs of my 120 gig hard drive :guitar:

Even the simplest questions never go unanswered here, thanks a lot :)

---

### Post by nicedude on 2008-08-13
You don't need a floppy or USB for DBAN, there is a CD image version that is only a few MB in size. I would recommend everyone have a DBAN boot CD in their arsenal of tools since it is the best FREE disk wiper ever. I have used it hundreds of times for several years and never had it fail to take care of wiping a disk properly. Assuming you dont actually have anything that someone will be taking the drive apart and using an electron microscope on it for, then remember to set to 1 quick pass - no verification so it doesn't take more than maybe an hour or so to do the wiping. But the one pass option will defeat all software based recovery tools and give you a nicely cleaned disk.  

Nice tip there from Sandy

---

