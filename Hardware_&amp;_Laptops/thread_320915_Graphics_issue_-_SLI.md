---
title: "Graphics issue - SLI"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by johimself on 2006-12-18
Hello there. I am new to Ubuntu (and indeed linux in general) but I am pretty good on hardware etc.

So Specs to begin with:
AMD Athlon 64 3700+ (overclocked to 2.64gHz) Socket 939
Asus A8N-SLI motherboard (Nforce 4 SLI chipset)
2x BFG 7800GT 256mb graphics cards in SLI configuration
2x Western Digital Raptor 74gb HDD (RAID-0) with 1 partition for Windows XP
1x Western Digital Caviar 80gb HDD (NTFS) with 1 partition for storage
2gb PC3200 RAM (Corsair and OCZ both same latency)

I recently downloaded Edgy and burned it to a cd. I cant get into Ubuntu. No matter what option i choose (safe graphics or normal) it wont get into the OS. all it gives is something similar to this artistic rendition:
[IMG]http://img510.imageshack.us/img510/3318/ubuntujq1.jpg[/IMG]

I have tried doing something involving pressing ctrl+alt+f1 to make this work (making the graphics driver a Vesa instead of a nv) but when I do this it simply removes the mouse cursor. The mouse responds up until I press ctrl+alt+f1 whereby it disappears. I assume that means it is making the terminal prompt but not drawing it on screen?

I would appreciate any help anyone can give on the matter. TBH this is why I have avoided Linux in the past (hardware incompatibility) and my laptop has disapointed as well (installs and works fine but no wifi making the fact that it is a laptop somewhat redundant)

Just to check I downloaded Dapper as well and the problem is the same (except the bacground is slightly darker - I assume that is the version rather than something to do with the problem.)

---

### Post by taurus on 2006-12-18
Looks like the LiveCD is having a little difficulty with your graphic card.  If you plan to install Edgy on your machine, I highly recommend you download and use the alternate CD instead.  It uses text base and you don't have to boot into a live session first before you can install it.  You install it right away from the menu when you first boot the CD...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by johimself on 2006-12-18
Thanks but do you know that when I install it it won't be a problem? My reasoning behind using the live version is to make sure it works before installation.

If using the text based installer is it best to partition the disks first?

Also with my RAID being configured in the NVidia raid controller will this be shown properly in the Ubuntu installer? I remember installing Fedora once and it saw my IDE Nvidia RAID as 2 disks and buggered up the windows install that was on them.

---

