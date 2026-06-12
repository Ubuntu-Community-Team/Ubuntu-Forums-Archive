---
title: "Which installation for EEE 2G 700"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by CrimsonEclipse on 2009-08-13
I haven the most basic of EEE PC's, the lowly 700 aka 2G.


Specs:
504mhz neutered CPU
512MB ram (no upgrade available)
2GB HD (no upgrade available)
8GB SDHC Flash card
External CD ROM available.

So, I'm presently using an Nlite'd version of WinXP installed onto the 2GB HD and I keep running out of room even running most programs from the Flash Drive. Now I'm looking for options. 

1. Which version of Ubuntu should I install?
Xbuntu, Ubuntu, Easy Peasy, 10 others I missed?

2. Should I install on to the 8GB Flash Drive and use the 2GB for Cache and miscellaneous files?

Thanks

CE

---

### Post by aysiu on 2009-08-13
If you're not afraid of doing a minimal installation of some kind (with a lighter version of Crunchbang or IceBuntu), then it's probably best to install Ubuntu to the 2 GB SSD and use the 8 GB SDHC for personal files.

If that seems a bit intimidating, you can just install Ubuntu on the 8 GB SDHC and use the rest of the SDHC and the SSD for file storage.

---

### Post by CrimsonEclipse on 2009-08-16
For the life of me, I cannot get ANY Ubuntu or Xubuntu to work on this thing.

Nor can I get ANYTHING to boot off the SDHC card. Even with the latest BIOS, no luck. 

I'm spinning my wheels here. As of now I'm reinstalling XP ](*,) Just to have SOMETHING work.

---

### Post by cbemerine on 2009-08-17
I am assuming that you either got your installation or gave up, either way there are many other Asus Eee PC users (yes even the Surf, 701 and 901) that are still using these netbooks) that would probably benefit from your experience.  I assume that you checked out all the install options offered on eeeuser.com; 

Here is a good comparison chart of what has been installed on the Eee PC: [http://wiki.eeeuser.com/overview.html;](http://wiki.eeeuser.com/overview.html;) Not a bad place to start.  

Currently I am still putting up with UNIONFS and the issues that it brings to the table, but not forever.  I plan to reformat the SSD drive and put on an ubuntu version built for the Eee PC, specifically the surf and/or 701.  (4G, 512MB RAM)

Check out that chart for the different distros that can be put on the Asus Eee PC.

---

### Post by cbemerine on 2009-08-17
Here are some more links to specific issues related to getting Linux and applications running on the Asus Eee PC that you and I have.  They are in no particular order:

                                            [http://eeepc-albkwan.blogspot.com/2009/06/create-asus-eeepc-system-recovery-usb.html](http://eeepc-albkwan.blogspot.com/2009/06/create-asus-eeepc-system-recovery-usb.html); 090603; Create an Asus EeePC System Recovery USB disk; ***
 
                                            [http://wiki.eeeuser.com/howto:usbrestore](http://wiki.eeeuser.com/howto:usbrestore); How to USB Resotre;  
  [http://wiki.eeeuser.com/backup_restore](http://wiki.eeeuser.com/backup_restore); Backup and Restore; 


UnionFS stuff (I have learned allot, but have not put this into practice yet.)  Intending too.

[LEFT]                                         [http://forum.eeeuser.com/viewtopic.php?pid=608398](http://forum.eeeuser.com/viewtopic.php?pid=608398); see gringos post about UnionFS and Aufs
  [http://en.wikipedia.org/wiki/UnionFS](http://en.wikipedia.org/wiki/UnionFS); wiki on UnionFS
 [/LEFT]
 

Firefox: from 2.0.0 first to 3.0.1 and than to 3.0.13 (I have not gotten FF 3.5 working yet on my Asus Eee PC 4G Surf but am planning too.)
[http://forum.eeeuser.com/viewtopic.php?pid=627213#p627213;](http://forum.eeeuser.com/viewtopic.php?pid=627213#p627213;) I posted some problems I experienced, but this was the best way to go that I found to get up to FF 3.0.13.


GIMP help
                                           [http://forum.eeeuser.com/viewtopic.php?id=41815&p=8](http://forum.eeeuser.com/viewtopic.php?id=41815&p=8); problems getting GIMP installed, this supposedly solves the issues.

---

### Post by CrimsonEclipse on 2009-08-17
Fair enough, but keep in mind, the 700 is MUCH more limited than the 701. 

I might try the EEEXubuntu. D/l ing now.

---

### Post by snowpine on 2009-08-18
> **CrimsonEclipse said:**
> I might try the EEEXubuntu. D/l ing now.

Big mistake... eeexubuntu is based on 7.10 gutsy gibbon, which has reached "end of life" and is no longer supported.

Aysiu gave the easiest response in post #2: install the current version of Ubuntu (or Ubuntu Netbook Remix) on the 8gb card.

---

### Post by CrimsonEclipse on 2009-08-18
I found 8.04 8.10 and 9.04 eeeXubuntu. 

And I tried to install on the Sdhc card but it will not boot from the card.

---

### Post by snowpine on 2009-08-18
I stand corrected... did not know eeexubuntu was still an active project... sorry!

Not sure if the 2g 700 is the same, but on my eee 900ha, you have to press Esc at boot to choose the SDHC card...

---

### Post by CrimsonEclipse on 2009-08-31
OK, I have finally been able to properly install Xubuntu on the flash drive. After install, I needed to change boot to the "removable storage" option and it seemed to work.  

Since the 504mhz Celery processor is so slow, I don't really see much of a delay in boot time or usage due to the use of the SDHC as the primary HD. 

For the time being, I'm leaving the Nlited WinXP on the 2GB primary HD in case of any special software needs. 

In hind site, I may have wanted to use the 2GB HD as the swap portion of the partition for increased speed. That might be suggested for those not using the primary HD as an extra O/S..

Cheers

CE

---

### Post by snowpine on 2009-08-31
> **CrimsonEclipse said:**
> In hind site, I may have wanted to use the 2GB HD as the swap portion of the partition for increased speed. That might be suggested for those not using the primary HD as an extra O/S..

Solid State Drives (SSD) are not recommended for use as swap, because they have a limited number of write cycles before they wear out. Swap is very disk-intensive.

A better way to improve performance is to make sure you keep your ram usage below the maximum. (512mb for you I think?) If you are using swap, it means you are out of ram. Swap is about 1000 times slower than ram. If you keep your memory usage down (for example by not opening too many applications at once), that's the best option.

Glad you followed up with the thread to let us know how it's going!

---

