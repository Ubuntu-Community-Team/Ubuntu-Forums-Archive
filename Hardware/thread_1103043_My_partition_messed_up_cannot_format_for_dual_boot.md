---
title: "My partition messed up cannot format for dual boot, cannot install xp, gparted cannot"
date: 2009-03-22
forum: Hardware
---

### Post by senyuman on 2009-03-22
I have a laptop ACER Aspire 4930. it has no OS installed at first. Then i installed Vista on the laptop.
 
The hard Disk is then partitioned into 3 primary partition with one logical/extended partition. C:/, D:/ E:/ and F:/. The extended partition is on drive D:/

Recently I try to install gOS which almost similar to Ubuntu (I believe) into one of the partition and also dual boot it with XP(and deleted the Vista after that). But before doing it I have did some adjustment to the partition in Vista Partition Manager. I shrink the D: drive and then I restore it again. I never had the experience using Partition Manager in Vista before but had the experience using GParted. I did not click any button during my resizing of partition in drive D. I just shrink it and then I extend it(restore to the earlier condition) without knowing is it the "resizing process has been done". becoz, in GParted, after making and action, the process of resizing will only start after I click apply button. I then try to chkdsk one of the partition and it says it cannot be done because the partition is in use. Then I just ignore it

After that I try to install XP, using XP pro sp2 CD. But after it loads the setup disk on boot, when it say  "Setup is loading Windows", suddenly it the BSOD screen appear. I try it with other XP CD, still giving the same results. So i thought the hard disk may be affected (damaged) by my action earlier. 

Then i install gOS into the hard Disk which i put in drive E:/. it went fine. So i decided to try to install XP back again. but then the same BSOD appear. then i remember about testdisk which i have used in my past experience. I used it in vista, but i dont look at the guide juz through my past memory. suddenly i have make it bad.

i checked in my vista partition, it only show C:/ drive. I am very afraid coz i dont make any backup. then i check in my gOS , it also appear only two partition C and gOS partition. then i ran again my testdisk in vista, fortunately, i found D: and F: drive. but the problem is with my D:/ partition, suddenly went wrong. it is said to be damaged and cannot be accessible from Vista, and the partition type is RAW. then i try to retrieve data from it using PhotRec, some of the data is alright, some of it has been corrupted. I ignore it bcoz i know there is no way i could retrieve it back. now my focus is to installed XP on the laptop.

i try to installed XP again but failed, then i did some searchin on net, i found out that there is a way, which require me to slipstream my XP CD with SATA driver for the 4930 acer driver. it can be used but then when it want to start the part of the setup it ask me to put SP1 Xp disk into it. I have to change the disk with other disk which have SP1 info in it.Then i try it and success halfway. it is because i am able to go until the stage which ask me to format the partition which i intend to install my XP(C:/). But my laptop doesnt seem to give me permission to format the partition coz the data is said to be damaged. then i deleted my D partition on the XP setup disk, then try to continue installation, but also it doesnt give the permission. i try to install it to different drive (D and E)but also gave me the same reason, the data has been damaged. then i just install it without formatting any drive. after that next problem arise, the copying part give many error copying and i just skip the files it want to be copied. about 30% of the files gives the error copying message which i skip the file, until some part, when finished copying, it stop loading for some time. 

i cancelled the setup and restart. then grub loader missing but i can access vista. in vista all the drive can be access except D: because i have deleted this partition during setup XP. then i try to look into gOS using live CD also try to look using gParted live cd, but suprisingly, both of them in gOS (partition editor and GParted live cd) shown that my hard disk is in the state of (unallocated space) which mans as if my hard disk has no partition at all from the very beginning.

i try back my TestDisk in vista, and after the ANALYZE part, it show that some error is happening which i dont remember but it say that the header of the cylinder is wrongly put. it should be put 255.This error message is appearing in two part which is the before first partition and before extended partition.Then i went to main menu in test disk, then change the head value of the cylinder to 255. then i reanalyze back, it shows only one error message regarding the geometry size of the head of the cylinder.
then i write the partition table back and try reinstalling xp without any success.

My head is now wanna explode with this kind of problem. any help is really appreciate.. sorry for the very longest explanation ever. 

Thank You.
Senyuman

---

