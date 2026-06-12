---
title: "Fiesty not recognizing RAID-5 array"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by KillerSiafu on 2008-02-21
EDIT: Running Gutsy not Feisty...

I setup a hardware RAID-5 array but ubuntu is seeing it as individual drives. I have a seperate hard drive that has the operating system installed and is not part of the array.

The hardware involved is:

Gigabyte - Nvidia 570 SLI Motherboard (onboard RAID controller)
AMD X2 6400+ Brisbane 2.5 ghz processor 
Four - 500 gb SATA II Western Digital Caviar HD's in a hardware RAID-5 array (healthy)
One - 160 gb SATA II Western Digital Caviar HD with Ubuntu loaded

I loaded gparted in hopes of formatting the array so I could mount it, but when I open the software, it sees 5 separate drives, not 1 drive + 1 large volume.

Any suggestions would be most helpful!

UPDATE: I found a link to a guide for setting up a RAID-5 array (software). Here's the link: [http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)
I would still like to know if this can be done with a hardware RAID setup.

---

