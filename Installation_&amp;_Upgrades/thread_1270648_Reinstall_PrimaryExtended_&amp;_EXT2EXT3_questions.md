---
title: "Reinstall: Primary/Extended &amp; EXT2/EXT3 questions"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by HousieMousie2 on 2009-09-19
I have been doing a lot of reading but I am still uncertain, so I want to run things by you all...

I have two hard drives, an IDE with Windows XP on it and a SATA with Kubuntu on it, and when I reinstall it will remain this way.

What I gathered is that you can have 4 primary partitions PER HARD DRIVE.

Not a problem for Windows, it has two partitions total.

Advice varies for Linux however.  Boot, Root, Swap and Home is how I have done it in the past, all 4 being primary.  But some people recommend adding partitions for var, temp and usr, without saying which (if any) should be primary, or if they are all logical partitions, or which extended partition should they be a part of... or what size they should be.

IF I am going to make var, temp and usr partitions, I would think they should be a part of the Root partition, making it an extended partition and var/temp/usr logical.

With 500GB of hard drive space to play with, I was intending to give 2GB to Swap (one half of my RAM size - my Swap is never used anyway,) 1GB to Boot, 30GB to Root and the remainder to Home.  Again, no idea what size var/temp/usr partitions should be.

Yes/No?  Good/Bad?


Format...

There was something of an argument about the format of Boot... EXT2 versus EXT3.  Leaving the many other formats out of the discussion here, I came away with the impression that EXT2 would be the best choice... the explanation was that journaling space would be wasted... unused on a Boot partition.

EXT3 used for all other Linux partitions (except, obviously, Swap.)

I do not want Windows to be able to read Linux files, period, so I will not be creating a NTFS/FAT32 partition on my Linux hard drive.  It is so rare that I boot into Windows, that I don't mind copying any needed files to the Windows hard drive before rebooting.

Any and all information or advice welcomed!

Thank you for taking the time to read this and doubly so if you also took the time to create a reply! :-}

---

### Post by raymondh on 2009-09-19
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Above for reference.

I see no reason for /var unless you are running a server.  However, your requirements may require so.

If you decide, then it is better to have those inside an extended (as logicals).  I would make /boot primary and ext2 but the rest (root, /home, /var, /usr, etc) be logical partitions.

At 500GB, kindly ensure that your BIOS can access that size or you risk the error 18.

Good luck, back-up and happy ubuntu-ing.

---

### Post by HousieMousie2 on 2009-09-19
> **raymondhenson said:**
> [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Above for reference.

I see no reason for /var unless you are running a server.  However, your requirements may require so.

If you decide, then it is better to have those inside an extended (as logicals).  I would make /boot primary and ext2 but the rest (root, /home, /var, /usr, etc) be logical partitions.

At 500GB, kindly ensure that your BIOS can access that size or you risk the error 18.

Good luck, back-up and happy ubuntu-ing.

Thank you, raymondhenson!

My BIOS can access the drive, as I am already using it... the reason for the reinstall is I am having frequent system crashes and am wanting to make a clean start (with the same hardware) just in case something has become corrupted.

I am not running a server, so I will happily not make a separate partition for var... thank you for that.

---

### Post by raymondh on 2009-09-20
> **HousieMousie2 said:**
> Thank you, raymondhenson!

My BIOS can access the drive, as I am already using it... the reason for the reinstall is I am having frequent system crashes and am wanting to make a clean start (with the same hardware) just in case something has become corrupted.

I am not running a server, so I will happily not make a separate partition for var... thank you for that.

you're welcome.  your partition sizes look good and generous.  happy ubuntu-ing.

---

