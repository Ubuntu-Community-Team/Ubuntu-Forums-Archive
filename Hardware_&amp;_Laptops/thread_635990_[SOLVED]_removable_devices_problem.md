---
title: "[SOLVED] removable devices problem"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by rustam_sandhu on 2007-12-09
i am a total new person to ubuntu and i am using gutsy

i am unable to connect my removable devices when i go 
removable devices and media menu in prefrences and ckick 
it i get the following error plz


The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.

plz help me its urgent

---

### Post by rustam_sandhu on 2007-12-09
i am a total new person to ubuntu and i am using gutsy

i am unable to connect my removable devices when i go 
removable devices and media menu in prefrences and click 
it i get the following error plz


The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.

plz help me its urgent

---

### Post by rustam_sandhu on 2007-12-09
i am a total new person to ubuntu and i am using gutsy

i am unable to connect my removable devices when i go
removable devices and media menu in prefrences and ckick
it i get the following error plz


The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.

plz help me its urgent

---

### Post by rustam_sandhu on 2007-12-09
i am a total new person to ubuntu and i am using gutsy

i am unable to connect my removable devices when i go
removable devices and media menu in prefrences and ckick
it i get the following error plz


The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.

plz help me its urgent

---

### Post by staticvoid on 2007-12-09
Go to "Places>Computer>*your drive*"

Where did you get your Gutsy Gibbon disk from? Did you download an ISO from Ubuntu.com and burn it to a disk? Did you geta prerelease version??

You should have the HAL service running by default. And you should have kernal 2.6

What external drive do you want to mount? Is it a SEAGATE?

try > sudo fdisk -l in a terminal while the device is connected and tell us the output.

No need to put 9 exclamation marks to get an awnser to your solution ;)

Hope you get it salve ASAP though.


static void

---

### Post by rustam_sandhu on 2007-12-09
i am trying to connect a usb pen drive its kingston
nothing happens wen i plug it in

---

### Post by staticvoid on 2007-12-09
ok. where did you get you ubuntu installation from?

---

### Post by barney_1 on 2007-12-09
Yeah, you don't want to post the same problem 4 different times in 20 minutes, not really the thing to do.  

Your other three posts:
[http://ubuntuforums.org/showthread.php?t=635997](http://ubuntuforums.org/showthread.php?t=635997)
[http://ubuntuforums.org/showthread.php?t=635990](http://ubuntuforums.org/showthread.php?t=635990)
[http://ubuntuforums.org/showthread.php?t=635991](http://ubuntuforums.org/showthread.php?t=635991)

Also, the title of this post should clearly summarize your post.

---

### Post by staticvoid on 2007-12-09
Go to "Places>Computer>*your drive*"

Where did you get your Gutsy Gibbon disk from? Did you download an ISO from Ubuntu.com and burn it to a disk? Did you geta prerelease version??

You should have the HAL service running by default. And you should have kernal 2.6

What external drive do you want to mount? Is it a SEAGATE?

try > sudo fdisk -l in a terminal while the device is connected and tell us the output.

No need to put 9 exclamation marks to get an awnser to your solution ;)

Hope you get it salve ASAP though.


static void

---

### Post by staticvoid on 2007-12-09
Go to "Places>Computer>*your drive*"

Where did you get your Gutsy Gibbon disk from? Did you download an ISO from Ubuntu.com and burn it to a disk? Did you geta prerelease version??

You should have the HAL service running by default. And you should have kernal 2.6

What external drive do you want to mount? Is it a SEAGATE?

try > sudo fdisk -l in a terminal while the device is connected and tell us the output.

No need to put 9 exclamation marks to get an awnser to your solution ;)

Hope you get it salve ASAP though.


static void

---

### Post by rustam_sandhu on 2007-12-09
i got it from the ubuntu website via bittorrent buddy
plz help me out:)

---

### Post by rustam_sandhu on 2007-12-09
i am sorry but plz help me its urgent:)

---

### Post by staticvoid on 2007-12-09
well, do what I said,

connect your pen drive and do ```
sudo fdisk -l
``` and post your results.

how long have you been using ubuntu? when did you burn the disk?

---

### Post by staticvoid on 2007-12-09
what is your kingston drive formatted to?

---

### Post by rustam_sandhu on 2007-12-09
these r the results


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03e103e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        7710    40957717+   7  HPFS/NTFS
/dev/sda3            7711        8337     5036377+   7  HPFS/NTFS
/dev/sda4            8338       12161    30716280    f  W95 Ext'd (LBA)
/dev/sda5            9613        9676      514048+  82  Linux swap / Solaris
/dev/sda6            9677       12161    19960731    7  HPFS/NTFS
/dev/sda7            8338        9126     6337579+  83  Linux
/dev/sda8            9127        9612     3903763+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7872     2015216    e  W95 FAT16 (LBA)


i burnt it today 
i have been using it for like 6 hrs
but its great to use looks lovely:guitar:

---

### Post by staticvoid on 2007-12-09
plug in your kingston pen drive and reboot your computer while it is still in.

theres problems with the drive and ubuntu.especially for  Kingston DataTraveler II

if you unplug it while the computers still on and plug it back, nothing will happen

VERY wierd, I know..

by the way, you have a ton of partitions :D

sv

---

### Post by staticvoid on 2007-12-09
if you get your data off it, then I'd recommend reformatting it.it might mount automatically then. gparted is good software for it.

sv[B]

(and now to page 2>> lol)[/B]

---

### Post by staticvoid on 2007-12-09
I found this:

> someonI had a Kingston Data Traveler pen drive that worked fine in Win98, XP, and OSX, but Ubuntu Warty would complain about "Invalid Media Values" and "Buffer I/O Errors" at the console when it was inserted, and it refused to Mount.
 
 I read this:
 [http://lists.debian.org/debian-user/2004/12/msg04382.html](http://lists.debian.org/debian-user/2004/12/msg04382.html)
 
 and figured that the parititon table was messed up on it. QTParted could repartition this pen drive, and then it would mount on the desktop ONE time only. None of my Windows utilities would repartition a USB pen drive, but my Mac's OS X Disk Utilities was happy to.
 
 So I used to to blow away the partition table and create a new UNIX partition. Then I slapped it into Ubuntu and it mounted. I unmounted it and reformatted it with: 
 #> mkfs -t vfat /dev/sda1
 
 and it mounted fine. Then I slapped it back into windows and reformatted it FAT32.
 
 Finally, I tried it again in Ubuntu, and it works fine now throughout all the platforms.
 
 My Iomega keychain drives, on the other hand, worked just fine on all the OSes right out of the box.e said this:


---

### Post by staticvoid on 2007-12-09
and watch this guys thread for awnsers,
[http://ubuntuforums.org/showthread.php?t=210186](http://ubuntuforums.org/showthread.php?t=210186)
maybe bump it with a polite: I'd like to know how too,

and this thread:
[http://ubuntuforums.org/archive/index.php/t-359.html](http://ubuntuforums.org/archive/index.php/t-359.html)

might get you some more awnsers

---

### Post by rustam_sandhu on 2007-12-09
thanks it worked 
thats coz i have xp installed and
i like my backups arranged in diff categories in diff drives
thanks buddy once again :):)

---

### Post by staticvoid on 2007-12-09
now be a good ubuntuforums user and mark this thread as solved ;)

your welcome,

it was fun doing all the rapid research for you.

---

### Post by beren.olvar on 2007-12-09
never mind

---

