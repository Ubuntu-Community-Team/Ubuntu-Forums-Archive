---
title: "External hdd Not Recognized"
date: 2010-01-13
forum: Hardware
---

### Post by gonsalvr on 2010-01-13
HP Pavillion hdd crashed in my daughters computer so I removed it and purchased a 2.5 USB 2.0 IDE Drive Enclosure and connected it to my laptop Asus Eeee running Ubuntu 9.10. I need to get access to the files on the external hdd and nothing seems to recognize except Palimpsest says:
Hard Disk 811 ATA/ATAPI Device
Unknown Size
Unrecognized
Smart Not Available
/dev/sdb

When I open a terminal and run:
rhg@rhg-laptop:~$ sudo parted /dev/sdb
rhg@rhg-laptop:~$ sudo gpart /dev/sdb
Floating point exception
rhg@rhg-laptop:~$ 

When I run Test Disk:  
Test Disk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
  
Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 160 GB / 149 GiB - ATA ST9160310AS

It only recognizes the hdd in my Asus. 

So if the Ubuntu Disk utility can see the drive how to I get these tools to see it? 
I know for a fact the OS on the external hdd is Ubuntu 9.04 ext3 because I set this system up for my daughter. The gpu chip melted onto her HP motherboard and crashed her system. Now to add more excitement to this puzzle, the external hdd does have the Captain Hook and the Aligator loud Tick Tock sound when you first plug it in so the hdd is not the healthiest either. 
rhg 



































































































































































































































TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 160 GB / 149 GiB - ATA ST9160310AS

---

