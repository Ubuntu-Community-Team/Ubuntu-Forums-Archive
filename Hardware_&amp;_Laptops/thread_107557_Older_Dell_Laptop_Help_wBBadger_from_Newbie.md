---
title: "Older Dell Laptop Help w/BBadger from Newbie"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by White Rabbit on 2005-12-23
I have a Dell Inspiron 3800 (circa 1999) that, after finding BBadger, would like to  try as an alternative to Windows.  This laptop runs @ 500 MHz (Celeron) w/364 mg RAM and a 4 G HD.  I want to wipe my HD clean and do an install with this OS only.  Does this seem reasonable???   What is the best way to reformat my HD (FAT32 v NTFS???).   Do I need any additional software to do a "new" install????

Any advice appreciated.

---

### Post by afhp on 2005-12-23
Hardware-wise, this machine should be fine. 

If you don't care about keeping Windows, wiping and repartitioning the disk is the best and easiest way to go. You'll be given the option when installing. 

Regarding formatting, FAT and NTFS are Windows-centric ; they might be useful on a dual-boot machine in order to exchange files between the two systems, but on a Linux-only setup they're not needed. When installing Linux you'll be offered a choice of disk formats, I'd recommend "ext3" or "reiserfs". 

Before you install, you might want to boot with the Ubuntu LiveCD to check how well the hardware is supported (this is especially important on a laptop). 

When you're ready to install, the Install CD is all you need for a basic system (OS, graphical shell, basic applications including web browsers and office). If you ever need more software later on you can always download it.

---

### Post by kingsidy on 2005-12-23
like afhp said, the most common linux file systems are ext3 and reiserfs. For a laptop that old, i would recommend to wipe the whole hard drive when installing, instead of trying to dual boot. Also you might think about using XFCE instead of gnome or KDE. It will run faster because it is smaller and less demanding than the other too, above all it takes little space. that way you can put the rest of those gigs to good use. You can try a basic server install, and then add XFCE, or whatever else you might want. Add anything else u need as they come. I have installed ubuntu on a friend's computer so that i can use it instead of windows. I used a 3.5 gig partition. I did a server install, then added XFCE. The computer has 384 MB ram. Runs fast and i got most of the little things that i use installed on it.

---

### Post by White Rabbit on 2005-12-23
Thanks guys.  My main goal here is to get away from MS OS with something that is stripped down but still powerful.  I don't want a dual boot system.  The laptop is my secondary computer and your suggestions are a great place to start.  I'm awaiting my CDs in the mail (download time here in The Great White North is about 10 hours).  Once I get up and running I'll be visiting the forums for software for the types of programs I need (Photo Manipulation, Statistics, GIS, etc.).

---

### Post by mcwtlg on 2005-12-23
I got it to run on a Dell CS series (400 mhz, 128 megs of RAM 6 gig HD).  It can be done, even with a pretty graphical shell.

It currently runs on 2 HP Omnibooks (one 650 mhz and the other 700 mhz) with 256 megs of RAM, tweaked as well as I can get it (with my limited intelligence).

Shiny.

---

### Post by afhp on 2005-12-24
[QUOTE=White Rabbit]Thanks guys.  My main goal here is to get away from MS OS with something that is stripped down but still powerful.[/QUOTE]

Then KDE or Gnome are probably a bit too much. Xfce is a good choice, or Window Maker, or fluxbox. Have a look at [http://www.xwinman.org](http://www.xwinman.org), try and pick the window manager that suits you best.

> I'll be visiting the forums for software for the types of programs I need (Photo Manipulation, Statistics, GIS, etc.).

Photo : the obvious reference is the Gimp (if you don't require print color-matching). GIS -- I'd say the GRASS package is the most powerful. Stats I don't know.

---

### Post by stalefries on 2006-04-29
I have the same model, with a 6 gb hard rive, and 256mb of ram, and Gnome runs just fine. Of course, it's not good for gaming and stuff, but it wouldn't be good for that on windows either. Go for the regular install, it should go fine.

---

