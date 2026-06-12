---
title: "[SOLVED] cannot mount hard disk"
date: 2008-08-02
forum: Hardware
---

### Post by aisar190 on 2008-08-02
i have 500gb hd by wd....i usually used it in windows....but when i want to put on ubuntu....it says...cannot mount device....what is the problem ?....i used it as external hard drive.....

---

### Post by logos34 on 2008-08-02
this is a usb external?

post output of this command:

sudo fdisk -l

---

### Post by aisar190 on 2008-08-02
> **logos34 said:**
> this is a usb external?

post output of this command:

sudo fdisk -l

here is the output..

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa313a313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2314    18587173+   7  HPFS/NTFS
/dev/sda2            2315        2618     2441880   82  Linux swap / Solaris
/dev/sda3            2619        4864    18040995   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d086485

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x455e9d9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS
...
anything ?

---

### Post by bigbrovar on 2008-08-02
from what u have posted .. u appear to have 3 different drives on ur system 

the way linux name drives is thus
it uses letter just like in windows e.g in windows u have drive c,drive d , etc
 on linux u have 
sda = for the first drive
sdb = for the sceond drive
sdc = for the third drive
etc
if say the first drive have one that one partition the partition are representated by numbers like sda1,sda2 etc

going to ur out put here are ur drives

**Disk /dev/sda**: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa313a313
[B]
the first drive[/B]

Device Boot Start End Blocks Id System
**/dev/sda1** * 1 2314 18587173+ 7 HPFS/NTFS
**/dev/sda2 **2315 2618 2441880 82 Linux swap / Solaris
**/dev/sda3** 2619 4864 18040995 83 Linux

**the 3 partitions on the first drive most likely ur linux file system** and an NTFS drive which is what windows uses 

**Disk /dev/sdc**: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d086485

Device Boot Start End Blocks Id System
/dev/sdc1 1 38913 312568641 c W95 FAT32 (LBA)
**the second drive**

**Disk /dev/sdb**: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x455e9d9b
**the third drive**

Device Boot Start End Blocks Id System
**/dev/sdb1** 2 60801 488376000 f W95 Ext'd (LBA)
**/dev/sdb5 2 **60801 488375968+ 7 HPFS/NTFS
[B]the other partitions on the last drive 

can u confirm this cus sumtins linux sees ur drive but doest mount it ..

reading ur initial post .. u said a 500gb hard drive

the there is only one 500gb  hard drive on ur system and its on /dev/sdb 

[**B]Disk /dev/sdb**: 500.1 GB,[/B] 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x455e9d9b
 could be the drive u want to mount .. do u get any errors when u plug it in .. like if go to /places/computer and check if u can see the drive there if u do .. try double clinking it .. and tell me what happens ..if not let me know

---

### Post by aisar190 on 2008-08-02
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x455e9d9b

this is the hard drive....i got 2 external...the 320gb is wd passport...and the 500gb is the one cant be mount in linux....its wierd...it shows here.....:(

---

### Post by bigbrovar on 2008-08-02
did u go to /Places/Computer to see if it is there .. sumtin an harddrive may not be mounted because it wasnt properly removed on windows.. if its there and u try to double click and it gives u an error .. then we will have to forcefully mount it .. if its not there then we will mount it all the same .. either way .. ur problem will be solved and u would have learnt one or two things about linux . :)

---

### Post by aisar190 on 2008-08-02
here is what happen.......
i provide u the link...once i tried to click on the icon......

[http://picasaweb.google.co.uk/aisar190/Ubuntu/photo#5229867831039995074]("http://picasaweb.google.co.uk/aisar190/Ubuntu/photo#5229867831039995074")

---

### Post by bigbrovar on 2008-08-02
just as i guessed .. the problem is because u didnt **safely remov**e the drive from windows .. properly .. 
solution
i was about posting a commnad that would forcefully mount it for u .. then i saw some chinese characters hs the name of the drive which i can type on my keyboard :(
 but try plugging the harddrive to a windows machine then at the bottom of the windows taskbar click the usb icon and safely remove it .. then plug it into ur ubuntu machine and it should work 

if it doesnt .. the we just have to use the last trick i have .. but try that first

---

### Post by nnamdi on 2008-08-02
do you what, you will have to go back to windows then safely remove it before bring it back to ubuntu cos it ones happen to me and that was how i solved it try that and see

---

### Post by aisar190 on 2008-08-02
> **bigbrovar said:**
> just as i guessed .. the problem is because u didnt **safely remov**e the drive from windows .. properly .. 
solution
i was about posting a commnad that would forcefully mount it for u .. then i saw some chinese characters hs the name of the drive which i can type on my keyboard :(
 but try plugging the harddrive to a windows machine then at the bottom of the windows taskbar click the usb icon and safely remove it .. then plug it into ur ubuntu machine and it should work 

if it doesnt .. the we just have to use the last trick i have .. but try that first

thx dude...its solved......

---

### Post by bigbrovar on 2008-08-02
glad it worked out well .. for a while when i didnt hear from u again i thought maybe the worst had happened :) .. anyway nice to know that it went well .

---

### Post by rykel on 2010-06-30
Guys, I have a similar problem.

When I plug in my external hard disk, I get an error. (see screenshot)

I have to manually mount it using Storage Device Manager all the time.

Please help?



UPDATE

I solved my own problem!

Simply purge 3rd party drive managers (eg. Storage Device Manager), comment out all the NTFS lines in /etc/fstab, do a "sudo blkid", reboot, plug in the devices and let Ubuntu auto-detect/auto-setup the UUID of the devices. I hope this solves your problems too!

The problem seems to be due to the fact that Lucid does NOT use /dev to identify devices anymore, and uses UUID instead.

---

