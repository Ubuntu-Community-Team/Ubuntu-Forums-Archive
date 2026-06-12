---
title: "Will Ubuntu Install / Run Well on a Portable HDD?"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by Jbanicar on 2007-12-10
Could someone tell me if a regular portable HDD with plenty of space, would run a partition of Geobuntu (or Ubuntu) well if connected to my laptop via USB?

 I've run two games off of my portable HDD, and it works quite well (Universe at War: Earth Assault demo / Acquaria).  I know the load times would be slightly longer, but wouldn't it still be possible?  It's still a hard drive at heart, right?

Specifically, I want to put Geobuntu on there, because I already have a Linux distro partition on my laptop (XPS Gen 2, the old model).  
 

Thanks

---

### Post by julianmh on 2007-12-10
> **Jbanicar said:**
> Could someone tell me if a regular portable HDD with plenty of space, would run a partition of Geobuntu (or Ubuntu) well if connected to my laptop via USB?

 I've run two games off of my portable HDD, and it works quite well (Universe at War: Earth Assault demo / Acquaria).  I know the load times would be slightly longer, but wouldn't it still be possible?  It's still a hard drive at heart, right?

Specifically, I want to put Geobuntu on there, because I already have a Linux distro partition on my laptop (XPS Gen 2, the old model).  
 

Thanks
It would probably work as long as Ubuntu recognizes the portable HDD. Operating systems are portable if they can be put on a live CD. I would reccomend putting the LiveCD version on the PHDD first.

---

### Post by Jbanicar on 2007-12-14
Update: My SimpleTech (230GB) portable HDD is seen as "bootable" by the BIOS (Dell XPS Gen2).  Everything with the installation went well off of the Live-CD: I selected the 230GB partition (obviously the portable HDD since my internal is only 100 GB), and I used the Ubuntu install-partitioner to "resize" it from 230 GB to 219 (couldn't get exact 220, heh)... which means that it would "give" Geubuntu (Luna) 10 GB of space, riight?

 Anyway, the install went fine without a hitch, and I clearly noticed the blue portable HDD light flashing, which of course let me know that it was being accessed by the install (and not mistakenly another drive).

So I come back to my room like maybe 30min later (cause I had to run an errand) and it is finished.  I click "Restart" (HAVING already set my "USB Storage Device" as the 1st Boot Option). 

 
(please shield your innocent eyes for the carnage that follows, viewer discretion is advised)

Upon restarting, "Loading Grub........ Error21" WHAT?!  (nothing else works)  Ok... stay calm, reboot the laptop, turn HDD on/off... "Loading Grub.... Error 5"  (curses).  Check BIOS, everything looks fine, restart... (repeat)

[PANIC MODE] Ok, so I am about to head over seas next Tuesday, and I just killed my laptop.  OR did I?  Apparently not... to make a long story short, I did some panic Googling (sorry Goole, it is a verb now), and found Super Grub and used that to restore my Windows boot.  I have no freaking idea what happend.  I have plenty of experience installing Linux onto my laptop to try it out, as I already had Fedora8 running PERFECTLY fine as a dual-boot with Windows.  I didn't think that this would mess Geubuntu up, because I was going to install it onto my portable HDD (which showed up as Bootable in the BIOS).  I had already asked this question and read up about it, to educate myself before I did anything, and I have tried Ubuntu before a while back when 7.10 came out.  I just wanted to give Geubuntu a try cause of the E17 desktop manager looked pretty amazing.

 So... what gives?  I can still see that my internal HDD is still partitioned as it was with my dual boot along side Fedora8 (read: 85GB space, 13GB free, meaning the Fedora8 partition of 10GB is still there.... somewhere).  I plan on using my SGD (Super Grub Disk) to try and repair that boot file as well.  If I do this, it should give me access to my Fedora & Windows boot again, right? 

What went wrong?  =(

---

### Post by Jbanicar on 2007-12-15
Update:

When under Windows I can see an extra drive partition that it can't tell how big it is... but when I boot into my other Linux distro (which isn't Ubuntu), it reads it as a 13.0GB partition.....

FYI: Obviously you can tell that I got my Windows / Fedora dual boot to work correctly again.

However, I want to see if I can get the Geubuntu to work.  I believe that's what the 13.0 GB is... but how do I get that to work?

---

