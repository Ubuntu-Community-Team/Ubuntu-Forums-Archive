---
title: "external HDD stuck &quot;scan and fix&quot; windows issue"
date: 2013-06-26
forum: Hardware
---

### Post by indianwala on 2013-06-26
Hello Friends,

I have an 80GB external hard disk with 75 gb of data, when connected to windows prompt for "Scan and Fix" i did contiue with out fix but it irretated and Hit the Scan and Fix now Ext-HDD drive is not accessible able to see the drive with letter and trying to access prompt for formate i avoid and google a lot got lot of confusion.

before u answer let me expalin my trails.

1. chkdsk m: /f
shows raw formate

2. testdisk done analyse and search after that run chkdsk m: /f says ntfs but not catagoried

3. intall ubuntu and tried accessing no success

 vinod@vinod-PI945GCM:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b750b75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   102885375    51339264    7  HPFS/NTFS/exFAT
/dev/sda3       102887422   207732735    52422657    5  Extended
/dev/sda4       207732736   312578047    52422656    7  HPFS/NTFS/exFAT
/dev/sda5       102887424   203540479    50326528   83  Linux
/dev/sda6       203542528   207732735     2095104   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x44427a94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   204802047   102400000    7  HPFS/NTFS/exFAT
/dev/sdb2       204802048   414517247   104857600    7  HPFS/NTFS/exFAT
/dev/sdb3       414517248   624232447   104857600    7  HPFS/NTFS/exFAT
/dev/sdb4       624232448   976771071   176269312    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1   156301487    78150743+  ee  GPT


/dev/sda first harddisk
/dev/sdb sec hardisk
/dev/sdd thrid external 80 gb harddisk

4. run gprated and shows the attached screen.
with two partitions one FAT32 with EFT Lable and second NTFS with out no lable but data space 75gb which i want my data back.

please help me to get the data safely.

---

### Post by trevm999 on 2013-06-26
Was this hard drive originally used with a Mac then reformatted using Windows?

---

### Post by Mark Phelps on 2013-06-27
In guess my first question is HOW an 80GB drive got formatted using GPT!!  I can see a 3TB drive formatted that way, but 80GB drives are OLD .. and they would (by default) be formatted using MBR.

IF you really want to recover the files, then you need to consider using Windows data recovery apps. You will need to connect the drive to a Windows PC to do this.  You could try Recuva -- which is free.  But, you would probably do better using RecoverMyFiles from Runtime Sofware, which is free to install and try, but you have to purchase a license online to do the recovery.

---

### Post by dannyboy79 on 2013-06-27
before you continue on with anything at all I would use ddrescue and make a backed up image of the drive and save that somewhere safe, that way as you're playing around with the drive and you really screw something up you at least still have a copy of the drive somewhere.

can you clarify, did you install ubuntu onto the 80GB hard drive or do you mean you tried accessing the 80GB hard drive from within ubuntu?

---

### Post by indianwala on 2013-06-28
> **trevm999 said:**
> Was this hard drive originally used with a Mac then reformatted using Windows?

Yes, I tried [COLOR=#444444][FONT=arial]**iAtkos **[/FONT][/COLOR]Mac and after that reformatted in dos mode.

---

### Post by indianwala on 2013-06-28
I tried with two types of Recovery software's none worked well or recovered files. So i installed ubuntu on my 160 GB HDD second partition and connected the 80 Gb HDD. I haven't get auto detect the connected drive so i checked with sudo fdsik -l and i found 80GB is detecting with /dev/sdd1 but shows as GPT.
when i check in windows and run the command chkdisk /f it says raw format. I tried with Test Disk and attached the screen shots and after  that run the command chkdisk it says NTFS but not opening. 
for you informatoin my hdd is showing but asking for format before i do it I am trying with Test Disk noting is help full. 
I also added the attachement of Gparted it shows two partitions in Ubuntu.

Please help

---

### Post by Mark Phelps on 2013-06-28
It's unlikely that any Linux utility is going to work.  I already told you what you need to do back in post #3.

---

### Post by trevm999 on 2013-06-28
Ok first we need to make an exact backup. You will need to install ddrescue in ubuntu and and have enough space to store an 80GB image, or another hard drive 80GB or more to be the backup.

```
sudo apt-get install gddrescue
sudo apt-get update
```

Now that ddrescue is installed, let's double check our drives with 
```
sudo fdisk -l
```

According to your previous run of fdisk, the 80GB drive was at /dev/sdd also take note that the drive has 156301488 sectors. If you connect another drive for the image, it might be located at /dev/sde

If you want to make an image and save it to your 500GB drive you will want to mount that drive then switch now to that drive i.e ```
cd /media/sdb4
``` this may be different so make sure you check the mount point of your drive.

To make a backup as an image run this command (as long as the drive is still /dev/sdd)
```
sudo ddrescue -n -v /dev/sdd imagename.img logfilename
```
imagename and logfilename can be changed to whatever you want

if you want to clone it to a HDD use this command
```
sudo ddrescue -f -n -v /dev/sdd /dev/sde logfilename
```
sdd and sde will change depending on where your drives are installed, so double check fdisk and double check your command. The first drive is your source. If you get it backwards your data will be overwritten.

Assuming the backup completes without error, we will be able to continue. If if does indicate an error let it complete and I can give you further commands to try and get a complete clone.

Sometimes ignorant software will reformat a drive as MBR NTFS, yet leave the GPT sectors alone. This really confuses Ubuntu. However, this does not really explain why Windows wanted to scan and fix your drive in the first place, since after this happens Windows usually just sees the drive as MBR NTFS. To get rid of GPT and allow Ubuntu to see the drive properly, we have to rewrite sector 1 and the last sector of the hard drive, which is sector 156301488 in your case. 


```
dd if=/dev/zero of=/dev/sdd bs=512 count=1 seek=1
dd if=/dev/zero of=/dev/sdd bs=512 count=1 seek=156301488
```

Now run fdisk and see what Ubuntu says about your drive. 

Please note that this assumes that you reformated the drive with a MBR partition table.

---

### Post by Mark Phelps on 2013-06-29
trevm999: 

Sorry to tell you this, but fdisk does not work with GPT formatted drives.  I believe there is something know as gdisk that does, but I'm not sure.

---

### Post by trevm999 on 2013-06-29
My use of fdisk here is just to find the drive location. But yes, it wouldn't be very useful if there were two or more GPT drives connected and they were the same size. 

This would be a more appropiate command to run in such a situation:
```
lsblk -o name,label,size,fstype,model
``` 

My assumption here is that the drive is supposed to be MBR and not GPT, therefore what fdisk says at the end is relevant. It is possible the MBR may need to be repaired afterword,

If my assumption is wrong, they you are right that the best option is data recovery software, preferably use on a clone of the drive incase the drive is failing and that is what caused part of the problem. Recuva is a good free option, but taking it somewhere that has RStudio would probably provide better results.

---

### Post by indianwala on 2013-07-01
Hi friends,
[CENTER]I am recovering of my 80 GB data with PhotoRec utility and im getting the files but not in structure with folders. Is there any other Recovery software that i can take see with folders exist on hdd and selected files and folders only get recover... 

[/CENTER]

---

### Post by dandnsmith on 2013-07-01
If you can get the files, then save them somewhere and worry about the folder structure later - recreate it is probably the best.
Once saved, delete the partitions, create a new MBR partition table (I think gparted will do this), and, if you want NTFS filesystems/partitions, format then on a Windows system before putting back the files in your desired structure.

NB It isn't a good idea to start a new thread on the same topic while one is running

---

### Post by Mark Phelps on 2013-07-01
> **indianwala said:**
> Hi friends,
[CENTER]I am recovering of my 80 GB data with PhotoRec utility and im getting the files but not in structure with folders. Is there any other Recovery software that i can take see with folders exist on hdd and selected files and folders only get recover... 

[/CENTER]

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by indianwala on 2013-07-04
I am scanning my 80 GB HDD with 7-data-recovery[FONT=Segoe UI, Tahoma, sans-serif][COLOR=#000000] &  [/COLOR][/FONT]iCare Data Recovery Pro 5.1. but still under scanning from last two days.. 
when i tried with Testdisk the data which i was expecting wasn't came. hope this could do.

---

