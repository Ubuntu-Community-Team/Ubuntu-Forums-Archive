---
title: "ntfs partition missing when I installed ubuntu mate 14.4"
date: 2015-04-09
forum: Hardware
---

### Post by nima7 on 2015-04-09
Hello everyones,
I had a windows 8.1 installed on C partition of my laptop. I had 2 partitions, C and D. Recently I installed Ubuntu mate 14.4. but I dont know how to find my files on D partition. Should I mont or something?
Any help would be appreciated...
I think the following information would help :

sudo fdisk -l :
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00087858

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1465147391   732322817    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1465147391   732322816   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 745.8 GB, 745789194240 bytes
255 heads, 63 sectors/track, 90670 cylinders, total 1456619520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4106 MB, 4106223616 bytes
255 heads, 63 sectors/track, 499 cylinders, total 8019968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table


```

df -h :
```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  684G  3.3G  646G   1% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        388M  1.2M  386M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  292K  1.9G   1% /run/shm
none                         100M   48K  100M   1% /run/user
/dev/sda1                    236M   36M  188M  17% /boot


```

sudo blkid :
```
/dev/sda1: UUID="56fa0875-40d6-4bbd-ae2a-f3e85341c44a" TYPE="ext2" 
/dev/sda5: UUID="tQJELc-qT2m-xBFV-RfHJ-f7Vj-LIIn-KpAQ0Q" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="8f775671-a8d4-42b1-9ea4-90a7b7899c36" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="61daad35-5ff4-4417-b3b6-cbd0943e6a0f" TYPE="swap" 

```


fdisk -l | grep NTFS :
```
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```

---

### Post by yancek on 2015-04-09
I don't know why you selected to use LVM to install Ubuntu but it overwrites everything.  Look at your fdisk output.  There are no windows partitions.  You would be better off using the install Alongside option if available or even better the manual method which is referred to as "Something Else" in Ubuntu.  The second option would have given you control of the installation.  You might be able to get data off the drive with something like testdisk but in all likelihood, you will need to reinstall windows.

---

### Post by nima7 on 2015-04-10
My disk have 1 partition now and it's logical linux format. If I wants to reinstall windows I should format disk. Is there any way to restore my files? I need them very much. Can you please help me? or show me the annother way?

---

### Post by yancek on 2015-04-10
If you want to try to recover data, stop using the installed system as every time you boot up and use it you will be overwriting more data.  If you use the windows installation media or a Recovery disk, it will just set it back to factory defaults and I don't think it will save any data.  TestDisk might work.  You can go to the site below which has Step by Step instructions on using it.  Scroll down the page to "Test Disk and Live Rescue CD" link.  It lists a number of ways you can get it on a bootable CD such as GParted or SystemRescueCD.  Better to use that than to boot the installed Ubuntu.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Bucky Ball on 2015-04-10
Reinforcing what yancek advises: Stop using that disk if you want to retrieve data from it. When you delete data, the data remains but the area where it is stored is marked as 'writable'. So, the data will still be there, but if you keep using the disk then you are writing over it as where it is is now marked as available for new data. Good luck. Testdisk or Photorec should do the trick. 

Testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Mark Phelps on 2015-04-10
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

