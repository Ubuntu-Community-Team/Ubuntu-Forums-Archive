---
title: "Only 30 GB of 700 GB external USB-Hard Drive used"
date: 2012-06-01
forum: Hardware
---

### Post by Yora on 2012-06-01
I very successfully installed Ubuntu 12.04 on an external USB Hard Drive [using this installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and after running the auto-updates, everything is running perfectly.
However, in "System Information" disk space is listed as 30 GB.
When I access the drive through windows, it said 600 GB with only about 1% used. (It did, right now windows refuses to detect it, when I plug it in.)

I did reformat the entire drive to FAT32 and ran the installer again and that time setting a persistent file size of 2 GB, but the only change was that the indicated disk space was listed as 30 GB instead of 20 GB at the first try.

Any idea why this happens and what can be done about it? I'd like to have the entire USB-drive available.

Update: I learned that Ubuntu only reserves up to 30 GB for system files. However, I am now running out of disc space as I am installing additional programms and plugins. Starting gparted, it shows the Drive as a single partition of 596.17 GiB with 33.52 GiB used.
In "System Setting" on "Details" it says "Disk: 3.1 GiB"
In "Home Folder", the drive appears as "casper-rw" but when I select it I get the error message "Could not find /cow". What does that mean?

Here is a [screenshot of the drive usage]("http://25.media.tumblr.com/tumblr_m4xurat3V31rud7mxo1_500.png"). "Backup" is a folder of my personal files also on the USB-drive.

---

### Post by TheFu on 2012-06-01
Sorry that I can't help, but the output of a command will help us understand your true situation:

$ sudo fdisk -l /dev/{device for USB drive}

This should show a list of all the partitions, their sizes and types on the USB drive .
Also, if you encrypted any of the partitions, that would be good to know too.

I haven't installed 12.04 on anything larger than a 10GB virtual machine, but other Ubuntu servers have many, many terabytes of storage here.  For most home users, there isn't any practical limit on partition sizes.  The defaults may be 30GB, which I doubt, but I could be wrong.

Personally, I try to keep the OS and Apps on 1 partition (10GB is plenty), /home on another and /var on yet another partition.  Keeping everything on a single partition when testing is fine, but when you commit to Linux, splitting these off is smarter.

---

### Post by darth62969 on 2012-06-01
my guess is that the drive is either failing or just not willing to cooperate with ubuntu... but from the sound of what was going on in windows it opened up 1 more possibility (which i think is unlikely) that you have a bad USB controller at a hardware level.

first i would run in windows command prompt CHKDSK (letter of drive):/ (or the ubuntu equivalent) that is if windows recognizes it. 

then run the drive manufactures disk utility in DOS or Linux to see if there is any issues with the drive. 

if these don't find a cause for the issue then plugin another USB drive and see if the computer will recognize it. if it does not then you have a mobo issue... and if it is only that drive then you have a dive issue (which should have been found by the previous steps.

---

### Post by Yora on 2012-06-01
I have now split the partition on the Drive and I'm now currently in the process of moving the packup files to the second partition, that should at least take care of the permanent "out of disc space" messages. There may be a chance that the OS just can't handle the 30 GB of space being filled with 33 GB of data and that this is the source of it acting weird.

I also noticed that I can't empty the trash bin. In right-click menus and other places, the option shows up, but is gray and can not be clicked.
Accessing the drive from windows, the trash folder is 11 GB in size.

---

### Post by Yora on 2012-06-01
I have now the new partition "Storage" on the hard drive and moved all the backup files there.
However, the Disk Usage Analyzer still can not handle it. [Screenshot]("http://25.media.tumblr.com/tumblr_m4y1y5WtYX1rud7mxo1_1280.png")

Gparted shows how it really is: [Screenshot]("http://25.media.tumblr.com/tumblr_m4y23iNiWe1rud7mxo1_1280.png")

The OS recognizes all the space on the drive, but is unable to comprehend that the total space is larger than 30 GiB.

Trash bin can still not be emptied, but I could just delete all the files by using Windows. Should I do that? It's 13 GB and would put the total amount of data on the drive at 28 GB. But would it make the directory structure completely go mad because it can't find files that should still be there?

> **darth62969 said:**
> first i would run in windows command prompt  CHKDSK (letter of drive):/ (or the ubuntu equivalent) that is if windows  recognizes it.
Here is the output, though I have to translate it from German (another  reason I want something else, all the guides are in English).

g:\ was the original partition for the entire drive on which the OS was installed with the Universal USB Installer.
h:\ is the new partiction I just created to store the backup data.
```
C:\Documents and Settings\User>chkdsk g:\
Typ of Data-systems is FAT32.
Volume PENDRIVE created 31.05.2012 19:50
Volume number: 1B0D-405B
Files and Folders are being checked...
File and Folder check completed.
Data system has been checked. No Problems detected.
  104.805.008 KB Memory Space(???) on the entire storage device.
        2.016 KB in 26 hidden files
        4.976 KB in 301 Folders
   15.330.096 KB in 5.733 files
   89.467.904 KB are available

       16.384 Bytes in each cluster ("dependency-unit" in German)
    6.550.313 clusters on the entire storage device
    5.591.744 clusters on the storage device available
``````
C:\Documents and Settings\User>chkdsk h:\
 Typ of Data-systems is FAT32.
 Volume STORAGE created 01.06.2012 15:36
 Volume number: 1710-1F52
 Files and Folders are being checked...
 File and Folder check completed.
 Data system has been checked. No Problems detected.
   520.209.472 KB Memory Space(???) on the entire storage device.
       14.336 KB in 52 hidden files
        12.032 KB in 187 Folders
    19.777.344 KB in 12.021 files
   500.405.696 KB are available
 
        65.536 Bytes in each cluster ("dependency-unit" in German)
     8.128.273 clusters on the entire storage device
     7.818.839 clusters on the storage device available
```I also ran this diagnostics tool, though I am still trying to get one from the manufacturer:
```
HDDScan S.M.A.R.T. Report 
Model: TOSHIBA MK6465GSX
Firmware: GJ003A
Serial: 308GF05PS
LBA: 1250263728

Report By: HDDScan for Windows version 3.3
Report Date: 01.06.2012 17:44:18


 Num  Attribute Name  Value  Worst  Raw(hex)  Threshold  

 001 Raw Read Error Rate  100 100 0000000000-0000 050 

 002 Throughput performance  100 100 0000000000-0000 050 

 003 Spin Up Time  100 100 0000000000-0A2B 001 

 004 Start/Stop Count  100 100 0000000000-0194 000 

 005 Reallocation Sector Count  100 100 0000000000-0000 050 

 007 Seek Error Rate  100 100 0000000000-0000 050 

 008 Seek time Perfomance  100 100 0000000000-0000 050 

 009 Power-On Hours Count  098 098 0000000000-03F6 000 

 010 Spin Retry Count  108 100 0000000000-0000 030 

 012 Device Power Cycle Count  100 100 0000000000-0194 000 

 191 G-sense Rate/Servo tracking  100 100 0000000000-0000 000 

 192 Emergency Retract Count  100 100 0000000000-0140 000 

 193 Load/unload Cycle Count  100 100 0000000000-13FA 000 

 194 HDA Temperature  100 100 38 C  000 

 194 HDA Temperature Maximum 100 100 48 C 000 

 194 HDA Temperature Minimum 100 100 13 C 000 

 196 Reallocation Event Count  100 100 0000000000-0000 000 

 **197 Current Pending Errors Count  100 100 0000000000-0009 000** 

 198 Uncorrectable Errors Count  100 100 0000000000-0000 000 

 199 UltraDMA CRC Errors  200 200 0000000000-0000 000 

 220 Disk Shift  100 100 0000000000-205A 000 

 222 Loaded Hours  100 100 0000000000-0067 000 

 223 Load Retry Count  100 100 0000000000-0000 000 

 224 Load Friction  100 100 0000000000-0000 000 

 226 Load-in Time  100 100 0000000000-0150 000 

 240 Heads Flying Hours  100 100 0000000000-0000 001 

```Highlight be me, that's the only item on the list that had "yellow" rating.



Apparently, Toshiba does not have any diagnostic tools.

---

### Post by oldfred on 2012-06-01
Is this a wubi install to a windows formated partition, or a liveCD/USB with persistence and not a full partitioned install. You should not be able to see any Linux partitions from Windows.

Post this.

```
sudo fdisk -lu
```

---

### Post by Yora on 2012-06-01
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc39cc39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   209712509   104856223+   7  HPFS/NTFS/exFAT
/dev/sda2       209712571  1953520064   871903747    f  W95 Ext'd (LBA)
/dev/sda5       209712573   415517260   102902344   83  Linux
/dev/sda6       419425088  1953520064   767047488+   7  HPFS/NTFS/exFAT
/dev/sda7       415518720   419424255     1952768   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdcfc5c58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   209712509   104856223+   b  W95 FAT32
/dev/sdb2       209712510  1250258624   520273057+   f  W95 Ext'd (LBA)
/dev/sdb5       209712573  1250258624   520273026    b  W95 FAT32
ubuntu@ubuntu:~$ 
```The g:\ partiation should have a LiveUSB installation made with Universal USB Installer.

Originally, the computer was as follows:
c:\ Windows files
d:\ empty space set aside for Linux
e:\ my personal files
g:\ the USB drive
h:\ the second partition I created on the USB drive, after the OS was installed.

The Trash Bin problem seems to have disappeared. I deleted the trash bin folder content manually while in Windows and when I now delete something in Ubuntu, I can empty it with no problems at all.

However, I have now reduced the total data on the drive to 27.3 GB, which according to the Disk Usage Analyzer is still 100%.
In "System Settings" on Details, it says "Disk 3.1 GB"
And I just notice that it's not 30GB but just 10% of it. That should be exactly the 3 GB I set aside for Ubuntu in the Universal USB Installer.

---

### Post by Yora on 2012-06-01
I found this: [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

This seems to be my situation, isn't it?

However, that seems to require that I am using Ubuntu on a hard drive different than the one I am currently on.
Which I currently can't do, since I [can't get Ubuntu running on the internal Hard Drive with Wubi]("http://ubuntuforums.org/showthread.php?t=1992946").

---

### Post by oldfred on 2012-06-01
The top entry in Disk Usage is always 100% as that is the total space you are reviewing. 

I do not understand g: drive, is that sdb1? Ubuntu uses drive like sda, sdb and partitions like sda1, sda2, sdb3 etc.

You have Linux partition in sda? Is that an install?

---

### Post by TheFu on 2012-06-02
Linux needs to be installed on a Linux partition, not FAT32 or NTFS unless you do a WUBI install. If you plan to use Linux for more than 20 minutes, don't use WUBI.

---

