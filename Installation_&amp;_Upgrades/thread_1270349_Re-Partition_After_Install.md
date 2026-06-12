---
title: "Re-Partition After Install"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by UnderPar on 2009-09-19
Hello,
 
Just installed 9.04 on my daughter's Compaq desktop. The 120 gig drive devotes 7.3 gigs on a hidden partition for recovery purposes.
 
I chose side by side, and went with the default partition size that Ubuntu chose to allot itself: 2.5 gigs. After install, I immediately chose Update Manager, which shows 154 megs of updates, but I get the "Not enough space" warning.
 
Obviously, 2.5 gigs is not sufficient, so I'm confused as to why Ubuntu would choose that as a default. How do I now re-partition that space? If that is not possible/good idea, how should I proceed? Caution: I am totally unfamiliar with Linux terms and commands - I strictly use my laptop version for surfing the web.
 
Thanks for anyone's help!

---

### Post by UnderPar on 2009-09-19
*bump*
 
16 views, but no one has offered an opinion yet.
 
Should I just use a program like [**Easeus Partition Master Home Edition 4.0.1**]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol")to erase the Ubuntu partition, and then start over?
 
Thanks.

---

### Post by gadolinio on 2009-09-19
To resize partitions, boot the computer with the liveCD. Then go to system-->administration-->gparted partition editor. That program gives you a graphic representation of the current situation of your hard disk. Right click the partitions and surf the menus to find the option of resizing.
I don't know exactly how the space is distributed, nor why ubuntu chose such a small partition. I only have 10GiB for the swap partition and the rest for the ext3 - ubuntu's one - and it works perfectly. But i can't tell you for sure what to do with yours; but gparted is the tool for doing it (and very easy to use, by the way).
Hope you find this useful...

---

### Post by raymondh on 2009-09-19
> **UnderPar said:**
> *bump*
 
16 views, but no one has offered an opinion yet.
 
Should I just use a program like [**Easeus Partition Master Home Edition 4.0.1**]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol")to erase the Ubuntu partition, and then start over?
 
Thanks.

Hi,

Yes, the 2.5GB install happens when the operator forgets to use the slider to allocate partition sizings when choosing side-by-side.

We can resize what you have now.  For that, we need to see either a gparted screenshot of your HD (access gparted thru system > admin > partition editor and then .... press prntscr key ... and then attach in your next post) 

or,  a terminal command output of
```

sudo fdisk -l
```

Another option is to redo. 

Drs305 wrote some good material for reference:

[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Back-up your files first.  Post back if you need a guide.

---

### Post by UnderPar on 2009-09-23
Thank you for the replies, but this is too technical for my limited Linux knowledge, as I mentioned in the OP.  I removed the partition and tried Wubi - again with no luck.

---

### Post by mecv on 2009-09-23
I had the same problem. I haven't tried repartitioning yet, but I have tried to reinstall ubuntu after deleting the previous partitions. The problem is that the boot menu (dual boot with xp) shows 2 entries of ubuntu, which by the way I haven't fixed yet. But everything will be okay other than that.

---

### Post by bruno9779 on 2009-09-23
@ UnderPar

Wubi takes in consideration older smaller HDD too, and by default chooses only 2.5 GB to install on. If I remember right the prompt also advises you to give at least 8 GB to Ubuntu.
Your best solution here is probably to start over, deleting the partition you have now and allocating it back to Windoze, maybe with a program like partition Magic.
Then you perform the wubi install anew.

@ mecv

Your Grub seems to need some cleanup.
To make sure it is only a grub entry you should post a screenshot of your HDD partition table in Gparted (as peviously advised).

After that you should post the content of /grub/menu.lst

so we can see if there are inconsistencies or the double Ubuntu entry is just different kernel versions

---

### Post by UnderPar on 2009-09-23
> **bruno9779 said:**
> @ UnderPar
 
Wubi takes in consideration older smaller HDD too, and by default chooses only 2.5 GB to install on. If I remember right the prompt also advises you to give at least 8 GB to Ubuntu.
Your best solution here is probably to start over, deleting the partition you have now and allocating it back to Windoze, maybe with a program like partition Magic.
Then you perform the wubi install anew.
 
 
Bruno - thank you for replying.
 
It's a 120 gig drive, with only 7.5 gigs hidden as an XP recovery partition, and around 9 gigs for the fresh XP install.  There's around 100 gigs free.  So I don't understand why Ubuntu would default to 2.5 gigs.  I didn't get any prompts to make it larger.
 
I ended up starting from scratch, re-wiping the drive and re-installing XP, which went smoothly.  I then decided to try installing under Windows again, this time from the Ubuntu 9.04 disk.  [I encountered a new problem]("http://ubuntuforums.org/showthread.php?t=1273136").  Very frustrating.

---

### Post by rreese6 on 2009-09-23
Underpar,
Post number 2 is the easiest way.
read it carefully, print it out even.
put your install CD in the drive and boot off of it.
then use the menu (as post #2 shows) to find the program "gparted"
then run that.
it will show you the 120gig drive and how it is being used.
If there is no gray areas(free space), highlight the windows partition (box) and click resize/move button. if your linux partition is after the windows one (I believe it should be). then make space "after" when you resize, say 3000 (that would give you 3 Gigs additional). click ok
then click apply and wait.
once done, resize the linux partition to take up the free space.
click apply.
you are done. reboot, remove cd from cd rom drive and you will have more space for Linux.

---

### Post by UnderPar on 2009-09-24
Thank you to everyone for your help!

---

### Post by drs305 on 2009-09-24
Missed this thread until today, but for anyone who stumbles into this post and is still looking for a solution:

The option is to expand the Ubuntu system partition or reinstall and include an extra action in Step 4 (Partitioning) during the installation.  Here are the guides explaining how to do both.

EXPAND  /
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

2.5GB  INSTALL
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

---

