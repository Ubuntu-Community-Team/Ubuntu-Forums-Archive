---
title: "Jaunty not installing"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by JohannWeiss on 2009-05-08
I am having issues installing Ubuntu jaunty on my PC. A few days ago I downloaded and installed it on my laptop without problems. I then tried with the same disc to install it on my PC but I have been unable to get past the partition stage. My PC is running XP-SP2 and has two hard drives. XP is on an 80GB HD and I have data saved on a 250GB HD. I am trying to put Jaunty on a 30GB chunk split from the 250.
 

 Twice I have gotten to the partitioning stage of installing Ubuntu. I selected the 250 and attempted to shrink it by 30 GB. It then shows a status bar which never gets past 0% and eventually (~30min) fails. The installer is then unable to determine the amount of spaced used in either HD and must be aborted.
 

 I had several other issues trying to put Ubuntu on the PC. When accessing the disc from my computer, it froze windows three times. It also failed to boot more times then it actually worked, when in the drive and restarting. When it was failing to boot it would show a black screen with a cursor mark which simply flashed for ~10min and then windows would boot. Once it crashed into a text mode in the first install screen. It wouldn't accept any commands but created new lines each time I hit enter.
 

 After having all those problems I tested the disc in my laptop using Vista. It seemed to work every time I tried to access it.
 

 These are my specs:
 

 VIA K8T800Pro, AMD Hammer
 AMD Athlon 64 Processor 3000+
 1.5 GB DDR SDRAM
 NVIDIA GeForce 7600 GS

---

### Post by pastalavista on 2009-05-08
Next time you successfully boot to the live CD, open a terminal and type
```
sudo fdisk -l
``` and post the output here.

Is it the 64-bit version of Ubuntu? Have you ever had any trouble with any other CDs? How old is the drive?

---

### Post by JohannWeiss on 2009-05-08
Alright, I booted into the live cd and here's the output from the terminal:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65386538

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1fa24af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

I don't really understand what all that means, but maybe you can see something wrong with it.

It isn't the 64 bit version because my laptop isn't 64 bit and I originally used it to install on there. It is an old drive but I can't recall any real problems with it. If the drive is a problem is there a distro which will boot from DVD?

EDIT: I tried using my DVD drive to install and it got to the same partition stage and failed. After it gives the error message saying it couldn't repartition the space it lists the 250 GB HD as having 0 GB used (It's closer to 200 GB) and the 80 as unknown.

---

### Post by pastalavista on 2009-05-08
No, nothing wrong there. It would be a good idea to boot into Windows and defrag the disk you want to resize before you try to shrink it. Did you try resizing it with Ubuntu's partition editor before you started the installer or did you just use the installers partitioner? Try that first and if it won't work, try the Windows defrag. Make sure that everything is cleanly shut down and log out when you're finished with Windows so you'll be able to unmount and shrink it with gparted and then try, try again.

---

### Post by geraldvillorente on 2009-05-08
What kind of CD are you using? is it i386(intel-based processor) or AMD64(AMD 64-bit processor)? Sometimes problem may arise from here, so we need to consider the possible cause of the problem(s).

P.S. 
You can partition your 250Gb HDD using LiveCD-gparted partitioner. 

Howto:
* reboot your PC and boot it from Jaunty livecd.
* launch GParted and select your 250Gb HDD
* format the drive using ext3 filesystem(target drive for ubuntu) and leave the rest as NTFS and could be use as storage media for both XP and Ubuntu
* reboot again after you format the drive
* then select the ext3 partition and just select the "[COLOR="Blue"]use entire disk[/COLOR]" option

Hope this will help you....:)

---

### Post by JohannWeiss on 2009-05-09
Alright, I think the problem is here. I tried defragging the drive but it didn't really do much. Before and after it looked like there wasn't going to be any reasonably sized chunks. I went into ubuntu and used GParted anyway and it failed the log file is below.

From what I can gather the drive is too fragmented, but I ran this after defragging it in windows. Is there any applications that may do a better job?

GParted 0.4.3
 Libparted 1.8.8
    **Shrink /dev/sdb1 from 232.88 GiB to 208.47 GiB**  00:08:53    ( ERROR )             calibrate /dev/sdb1  00:00:00    ( SUCCESS )             [I]path: /dev/sdb1
start: 63
end: 488392064
size: 488392002 (232.88 GiB)[/I]          calculate new size and position of /dev/sdb1  00:00:00    ( SUCCESS )             [I]requested start: 63
requested end: 437192909
requested size: 437192847 (208.47 GiB)[/I]       [I]new start: 63
new end: 437192909
new size: 437192847 (208.47 GiB)[/I]          check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:13    ( SUCCESS )             

***ntfsresize -P -i -f -v /dev/sdb1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 196310 MB (78.5%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    200132 MB             0
Multi-Record       :    250057 MB         74709
$MFTMirr           :    125029 MB             1
Compressed         :    250052 M
B         44116
Ordinary           :    174683 MB             9
You might resize at 196309704704 bytes or 196310 MB (freeing 53747 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:08:26    ( ERROR )             run simulation  00:08:26    ( ERROR )             

***ntfsresize -P --force /dev/sdb1 -s 223842737663 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
New volume size    : 223842730496 bytes (223843 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 196310 MB (78.5%)
Collecting resizing constraints ...
Needed relocations : 3615308 (14809 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1048 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:13    ( SUCCESS )             

***ntfsresize -P -i -f -v /dev/sdb1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 196310 MB (78.5%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    200132 MB             0
Multi-Record       :    250057 MB         74709
$MFTMirr           :    125029 MB             1
Compressed         :    250052 MB         44116
Ordinary           :    174683 MB             9
You might resize at 196309704704 bytes or 196310 MB (freeing 53747 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:01    ( SUCCESS )             run simulation  00:00:01    ( SUCCESS )             

***ntfsresize -P --force /dev/sdb1 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
New volume size    : 250056700416 bytes (250057 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:00    ( SUCCESS )             

***ntfsresize -P --force /dev/sdb1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
New volume size    : 250056700416 bytes (250057 MB)
Nothing to do: NTFS volume size is already OK.[/I]

---

### Post by geraldvillorente on 2009-05-10
You can use Partition Magic under Windows. This is an all-in-one tool for HDD. Also, you can resize/format/convert(ext3/raiserfs/ntfs/fatxx) your partition even the drive is mounted.

---

### Post by Jekshadow on 2009-05-10
Same problem, but with one 500GB drive and Vista. One more thing, its been ~30 mins now and it still is saying 0%... no error message.

---

### Post by JohannWeiss on 2009-05-15
So I've spent the last four days trying to get my drive defragmented and it wont do it. Windows defragmenter couldn't fix very many of the files. I downloaded Smart Defrag and it also couldn't, but it told me why: there wasn't enough space to move the files around in. So I proceeded to delete as much as I could; the drive currently has 36% free of 250Gb. Still, neither program can do a good enough job to get me a 25Gb chunk.

Does anyone have any tips for defragmenting?

---

