---
title: "Hanging on partition part of install"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Dafong on 2009-10-09
I am trying to install Ubuntu on a PC with existing partitions and an existing install of Windows XP.

I choose my time zone and then choose the keyboard I wanted and I am sure it said something about Partitioning next, but I can see nothing on the screen right now to indicate that is what it is doing.
 
It is just hanging and has been for awhile now.
 
I am going to retry it before posting this.  No luck still gets to the part says Loading Partitioner and then jus sits there hanging.

Is this part of the process known for taking a very long time? 10mins + ?

---

### Post by scragar on 2009-10-09
It can on slow machines take a minute or two to scan the disks(especially if they are very large), but I doubt it's still functioning if it's taking longer than that.
Have you checked the disk(liveCD) for errors?

---

### Post by Dafong on 2009-10-09
> **scragar said:**
> It can on slow machines take a minute or two to scan the disks(especially if they are very large), but I doubt it's still functioning if it's taking longer than that.
Have you checked the disk(liveCD) for errors?
 
Yeah I used the installation CD as a LiveCD and it worked fine i was able to mess about on the desktop and check other files on other drives.
 
They are very large partitions already on the drive, roughly 300gig with 3x100gb partitions.
 
I think 10-15 mins is the maximum I have left it anything I can do to help it along?

---

### Post by Bartender on 2009-10-09
How much RAM you got?  I usually get partitioning screen in less than a half-minute on my P4 with 2GB RAM.

---

### Post by Dafong on 2009-10-09
> **Bartender said:**
> How much RAM you got? I usually get partitioning screen in less than a half-minute on my P4 with 2GB RAM.
 
I have an AMD+ 2.4ghz with 3gb of RAM.

---

### Post by raymondh on 2009-10-09
> **Dafong said:**
> I have an AMD+ 2.4ghz with 3gb of RAM.

Hi ... just curious ... can you access a terminal (applications > accessories) and type (as well as post back results of)

```
sudo fdisk -l
```

small L, not I nor 1

I'd like to know how many partitions you have existing and their respective types.  If you want, you can also access gparted (system > administration > partition editor) and just copy/post back.

Thanks.

---

### Post by Dafong on 2009-10-09
The other machine seem to be hanging when I try and run Gparted.  I am leaving it for a few minutes while I make this post.  Just incase it is just slow.
 
The results for sudo fdisk -l
 
Disk /dev/sda@ 300gb 255 heads, 63 sectors, 36483 cylinders
Units= cylinders of 16065x512=8225280
Device ---  Boot   Start End Blocks   - ID - System
/dev/sda1    - * --- 1 -- 12  - 97m  - 7   - HPFS/NTFS
/dev/sda2  ---------12--36  - 195m - f  - W95 Ext'd (LBA)
/dev/sda5 --------- 12 -24  - 102m  - 7   - HPFS/NTFS
/dev/sda6 --------- 24 -36 -- 92m   -  7   - HPFS/NTFS
 
And yeah Gparted is having none of it, it seems to have hung up the entire LiveCD now nothing seems to want to work on it.

---

### Post by Pumalite on 2009-10-09
Use Gparted Live CD:
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

---

### Post by Dafong on 2009-10-09
> **Pumalite said:**
> Use Gparted Live CD:
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
 
OK i started it with straight default settings and it is running now, tell me if I was supposed to do something else.
 
Thanks :)

---

### Post by Dafong on 2009-10-09
Since other people were saying that it started in just a very short while, I am going to have to go ahead and say....yeah the liveCD of just Gparted is also hanging.  Just nothing happening, just says "checking for dev/hda partitions" and a little graphical bar bouncing back and forth.
 
yeah been like 5 mins now, nothing happening.

---

### Post by Dafong on 2009-10-10
Ok.
 
No joy with Gparted at all in anyway, so what I have done is put in a Windows XP disk with the idea that I will format C: and then attempt Ubuntu again.
 
Perhaps it is just that C: is such a mess that Gparted can't work its way through it.  Also formatted it to NTFS (Full)
 
Will try again after that.

---

