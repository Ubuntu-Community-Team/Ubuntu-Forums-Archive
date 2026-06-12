---
title: "Ubuntu Locks up during installation"
date: 2008-07-18
forum: General Help
---

### Post by hajent on 2008-07-18
I purchased brand new blank disks yesterday and Ubuntu locks up after (Partition Manager)- opens- during installation.  My computer screen also goes blank.

I have tried installing Kubuntu but I can't even get past (Accept License Agreement) before it locks up, too.

1 GIG of Memory, AMD Athlon 3800+ and PLENTY of hard disk space.

Any ideas?

---

### Post by PmDematagoda on 2008-07-18
At what speed did you burn the images to the CDs?

---

### Post by hyper_ch on 2008-07-18
did you check the cds for defects in the boot menu?

---

### Post by Kevbert on 2008-07-18
Once you've downloaded the ISO file you should perform a hash check.  See how to [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM").  When you burn the CD you shuld use the slowest burn speed available (to minimize any errors while writing).  Next thing to check would be the disk integrity (via the menu that is displayed when you boot from the disk).  Finally a memory check on your PC should be performed (via the same menu).  The memory check should be run for at least one pass (Windows may still run even with some faulty memory, but you may get the occassional unexpected crash).  It no problems occur, welcome to the wonderful world of Ubuntu.

---

### Post by hajent on 2008-07-18
Checked the CDs for defects in the beginning with no problems discovered. Memory is fine and I burned at a slower speed to no effect.

Looks like I'm either going to have to find a different distribution or order free cds.  :mad:

---

### Post by hyper_ch on 2008-07-18
did you try noapic?

---

### Post by Potatoj316 on 2008-07-18
Ive had a similar problem but it was due to a lack of RAM.  Try runing the memcheck that the CD offers.  Maybe your RAM is damaged.  If you see any errors (they will be red) then you have some problems with your memmory.

---

### Post by danwood76 on 2008-07-18
You could always try the alternate install CD.
Its Ncurses based so no pretty GUI but its a nice looking install interface whcih is fairly similar to the X based one.

---

### Post by hajent on 2008-07-18
Okay, by alternate CD install do you mean hitting F4 and choosing (Alternate CD) install?  The only options I have when hitting F4 are : install using update CD and Normal .

I'm running a memory test right now.  I just used another CD burning application with the effect.  What's wrong with you Ubuntu?

In case anybody is interested, I was burning an ISO image with ImgBurn and reverted to CDBurnerXP but both had the same results.

---

### Post by hajent on 2008-07-18
The only options I have when hitting F4 are : install using update CD and Normal . Do I need to choose (Update CD)?

I'm running a memory test right now.  I just used another CD burning application with the effect.  What's wrong with you Ubuntu?

In case anybody is interested, I was burning an ISO image with ImgBurn and reverted to CDBurnerXP but both had the same results.[/QUOTE]

---

### Post by avtolle on 2008-07-18
The Alternate Install iso is obtained at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) as you scroll down the page, under the green arrow, there is a check box to indicate you wish to download that iso. It also needs to be burned as an image to CD at a slow speed, with the checks, etc., made as discussed previously. BTW, try to get the 8.04.1 iso, as that will save you some upgrade time after installing.

Do you have SATA drive(s) on your computer? This has been a problem for many.

---

### Post by Kevbert on 2008-07-18
> **hajent said:**
> Okay, by alternate CD install do you mean hitting F4 and choosing (Alternate CD) install?  The only options I have when hitting F4 are : install using update CD and Normal .

I'm running a memory test right now.  I just used another CD burning application with the effect.  What's wrong with you Ubuntu?

In case anybody is interested, I was burning an ISO image with ImgBurn and reverted to CDBurnerXP but both had the same results.

Please take a look at [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/8.04/switching/installing-burning.html").  Some Windows burning software is known to use different file naming conventions to Linux.  It may be worth trying the software mentioned on this page.

---

### Post by hajent on 2008-07-19
Yes I have an SATA H.D. but I'm trying to install Ubuntu on my IDE H.D; however, I disconnected the SATA H.D. during a new install to no avail.  I will try the alternate CD method and burning software mentioned by Kevbert.

I want to dumb Windows and use Linux- Work !!!!!

---

### Post by danwood76 on 2008-07-20
Burning an image is a raw process so using windows or linux or whatever to burn it should have no real effect.
DVD Decrypter is good for burning ISO's and is completely free.

The alternate CD should help you as I would assume it is having a problem with graphics or something else.

---

