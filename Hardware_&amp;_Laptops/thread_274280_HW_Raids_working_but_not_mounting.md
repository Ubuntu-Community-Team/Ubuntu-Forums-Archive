---
title: "H/W Raids working but not mounting"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by Urreality on 2006-10-09
I'm still quite a newbee to Ubuntu but I've been have this problem solid since the start. I have two raid arrays a High Point Rocket Raid 464 IDE raid 5 PCI card and a Silicon Image 3112 SATA mb-based controler.  
When I first tried installing linux, on a non raid drive, Feora Core, as is be, the second it trying accessing the High Point it locked up.  Same with Debian and Suse.  They loaded fine on my system if I pulled the High Point card but with it in the installer window locked up right away.  Ubuntu is the only distro that could even load with it plugged in.  And even tho I have both arrays set to be hardware controled, within linux, including with gparted live cd they are seen as a bunch of separate drives.  From the "Computer" link in the place menu it sees them but won't mount them.  (see image) [ATTACH]17203[/ATTACH]
The Disks module in the system/administation menu sees the partition allotment on the first disk. (see image) [ATTACH]17202[/ATTACH]  but also won't enable them.
The arrays work fine in windows and they are NTFS but I even tried reformating the sil3112 array in Ubuntu using the disk util and it would mount but had problems like not remounting next boot and if I when into windows is would still see it as a blank NTFS.  I need it to be fat32 or ntfs so windows can read/write, I just want linux to be able to read it. I tried installing the latest linux drives for the controllers but that requires configuring with the kernal build which is way over my head,  Not that it would nessisarily fix the problem.  
Please, any help would be great,

---

