---
title: "Partitioning Problems, Not enough room message"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by amwil1024 on 2006-01-14
Greetings All,

I'm chomping at the bit to get my Ubuntu going full steam, I'm doing a dual os install and when I get to partition amount for my existing os, well, here's the stats, 

I have a 12.74 GB HD with 3.18 used by my current os, (Win98SE) and I have been trying to partition with 7 GB going to my old os and the balance left for Ubuntu, well, here's the problem. I have gone as low as 4 GB for my existing os but continue to get the following message, "Not enough free space available to instal Ubuntu" I don't want to go lower than 7 for my existing os if at all possible, I will go lower if I have to though but as I understand it, that Ubuntu needs only 4-5 GB tops? I've got the next 6 hours to figure this out!

Please tell me what I can do!

Regards, Mike "Piedmont"

---

### Post by Mr_Grieves on 2006-01-14
What kind of installation are you trying? Full installation - all stuff possible? :)
If you're low on space, try doing a minimal installation and install more stuff that you need as you go.

---

### Post by amwil1024 on 2006-01-14
[QUOTE=Mr_Grieves]What kind of installation are you trying? Full installation - all stuff possible? :)
If you're low on space, try doing a minimal installation and install more stuff that you need as you go.[/QUOTE]

I'm doing a standard install, whatever the process loads. I don't know how to do a minimal install, but, like I said, I thought Ubuntu only required 3-4 GB. I didn't think Ubuntu was a bigger OS then 98SE with numerous software loaded in it!
How much GB does Ubuntu need?

---

### Post by munga_bill on 2006-01-15
G'day, what about trying out some other partitioner and see if that can do it better. The latest GParted is now on its own CD, it's great! 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Download the .iso from here and burn it to a CD. I have the the 0.0.9-Alpha 3 and it's really great! The 0.1 is out already, that's the latest version, and it's the first stable release, that should be able to do the job!
Of course you can use Gparted on the Ubuntu Breezy Live CD, but when GParted is on its own CD, it's a bit quicker and also likely to be more up to date. It's only a 33.9 MB download.
I'm not sure, but I think I read it can resize FAT32 whether it's defragged or not and even resize reiserfs, but I have yet to try those things out, so I don't know yet for sure. If it's true then GParted will be the most advanced partitioner I know of.

---

### Post by amwil1024 on 2006-01-15
Thanks Mate but I finally resolved my problems, see my latest post about "I"m In" I had to uninstall a program called "GoBack" which had made my HD partition a NON-DOS partition!

Regards, Mike "Piedmont"

---

