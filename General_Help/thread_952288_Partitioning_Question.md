---
title: "Partitioning Question"
date: 2008-10-19
forum: General Help
---

### Post by thestig_992 on 2008-10-19
I have ubuntu installed on a 250gb drive, taking up the whole drive. Is it possible to repartition the drive so i can install windows on a 50gb partition without damaging my ubuntu?

---

### Post by Prometheum on 2008-10-19
Yes; just boot off of a live CD and resize the partition. Be prepared for it to take a very long time, though. In addition, Windows will probably break Grub, so be prepared to reinstall that.

---

### Post by thestig_992 on 2008-10-19
So with fdisk i need to delete my current parition, make a new smaller one, then make another windows one, nad make an ext3 filesystem on the ubuntu one?

Or is there a resize partition tool?

---

### Post by M4rotku on 2008-10-19
There is a specific tool for partition editing contained within the live cd.  It is called gparted and is accessed in the following manner:

System -> Administration -> Partition Editor

It has a very intuitive GUI and you shouldn't have any problems with it.
Be sure to back up any valuable data before partitioning. :) and good luck

---

### Post by bodhi.zazen on 2008-10-19
Use Gparted, it is on the live CD.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by iwc5893 on 2008-10-19
> **bodhi.zazen said:**
> Use Gparted, it is on the live CD.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

+1 on Gparted.  I've used the live CD several times while trying to get my system just right, and it works great.

---

### Post by thestig_992 on 2008-10-19
kk will do. ty everyone

---

### Post by thestig_992 on 2008-11-01
ok, I have a new problem based on the same thing; when i try to install windows, it scans all my hardware, but then comes back saying i have a 13gig, or 130gig (cant remember...) hard drive, with no partitions, however what i actually have is a 230g drive with 210 g for ubuntu, and an empty 20g ntfs partition for windows, which i just created then with gparted.

I have no idea whats going on. I remember that originally i intended to install windows first on the drive then install ubuntu, because its easier imo, and i didnt want to risk breaking grub...
Anyways the point is that windows saw the exact same thing. I only have one hdd, and I have installed the same copy of windows on other hdds on the same comp, which all worked fine...

Any suggestions?

---

### Post by uidb4056 on 2008-11-01
This HowTo [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) may help you.

---

### Post by thestig_992 on 2008-11-01
I think I can manage that part of the setup thanks to gparted, but my real issue is still that windows wont read the drive properly. Unlike in the guide, windows didnt see any paritions on the drive, only 130g of empty space...

---

### Post by caljohnsmith on 2008-11-01
Is the drive you want to install Windows to a SATA HDD? If so, you'll have to make a special Win XP Install CD to deal with it. If that's not your case, I've seen where the Windows XP installer won't recognize a HDD properly because the HDD's partition table is slightly corrupt. So if you're not installing to a SATA drive, I would recommend checking the integrity of the partition table with testdisk. Let me know your situation and we can work from there if you want. :)

---

### Post by thestig_992 on 2008-11-01
Yeah it is a sata drive, how do i make a special cd?

---

### Post by caljohnsmith on 2008-11-01
See these links:

[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)

---

### Post by thestig_992 on 2008-11-01
hmmm...Seeing that I might just swap to Vista, which i was considering anyway. 
Ty for your help, I never would have guessed that windows didnt work properly with sata drives XD

---

