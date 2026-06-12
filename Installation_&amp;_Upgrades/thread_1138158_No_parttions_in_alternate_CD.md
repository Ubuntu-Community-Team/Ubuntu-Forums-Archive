---
title: "No parttions in alternate CD"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by apparle on 2009-04-26
I have 8.10 installed and want to try jaunty.
For some reason I can't boot to a live CD (I posted earlier but didn't get any replies)
In alternate /text install CD
When I reach the stage of partitioning HDD and select manual partitoning............I don't see any partitions, just the main HDD. So I cancelled the installation. I have checked the md5sums and the integrity

Here's the sudo fdisk -l output when I boot into 8.10
```
ap@PARLE:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3bae3ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda3            3825        5736    15358108+   b  W95 FAT32
/dev/sda5            1913        3493    12699319+  83  Linux
/dev/sda6            3494        3614      971901   83  Linux
/dev/sda7            3615        3824     1686793+  82  Linux swap / Solaris
/dev/sda8            5737        7648    15358108+   7  HPFS/NTFS
/dev/sda9            7649        9728    16707568+   b  W95 FAT32
ap@PARLE:~$

```

I want to dual boot with Windows XP as I had done with 8.10.

I have one NTFS partition for WinXP, another for some data.
Also I have 2 other FAT32 partitions.
I have one EXT3 partition with 8.10 installed and well working, a swap parition and another empty partition of 1Gb without any filesystem.

I just want to  fresh install jaunty on the EXT3 partition

What should I do to make the partitions manually

---

### Post by SourceV on 2009-04-26
I have a similar problem, only that I am using Kububtu 8.04 and trying to upgrade to Ubuntu 9.04.

In my case I am able to start the live CD, but when getting to the partitioning part, I cannot see any partitions. Same goes with the alternate CD.

When I run the live CD, I can see the various partitions on my laptop, using the file manager. however, they do not appear in the partition table.

Any suggestions?

---

### Post by groova on 2009-04-26
Just to keep this up there: I can confirm. I have stayed up all night to install XP (again) and was hoping for a quick afternoon session to install the amd64 version of Jaunty.

This is my fdisk:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bab9bab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        6197    29294527+  83  Linux
/dev/sda3            6198       24321   145581030    5  Extended
/dev/sda4           23572       24321     6024343+  82  Linux swap / Solaris
/dev/sda5            6198       23571   139556592   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb51093e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      101587    51199816+   7  HPFS/NTFS
/dev/sdb2          101588      484518   192997224    7  HPFS/NTFS
```

sda1 contains XP and sda2 contains Ubuntu 8.10 (32bit). 

So I installed XP (last night) into partition sda1 (incidentally the XP installer found all partitions, even if he couldn't read half of them). I then popped in the LiveCD of Jaunty and wanted to install.

According to the partitioner, sda is completely empty, while sdb has the proper partitions.

Funny thing, booting into the LiveCD I can access the drives on sda and after re-installing grub I can even still boot into the old Ubuntu install.

Any ideas anyone?

---

### Post by meierfra. on 2009-04-26
apparle:

Your partition table needs fixing. (the primary partition /dev/sda3 sits inside the logical partition /dev/sda2). Could you post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

for further help?

---

### Post by apparle on 2009-04-26
> **meierfra. said:**
> apparle:

Your partition table needs fixing. (the primary partition /dev/sda3 sits inside the logical partition /dev/sda2). Could you post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

for further help?

Here it is
```
ap@PARLE:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe3bae3ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sda2        30716280   156280319    62782020    f  W95 Ext'd (LBA)
/dev/sda3        61432623    92148839    15358108+   b  W95 FAT32
/dev/sda5        30716406    56115044    12699319+  83  Linux
/dev/sda6        56115108    58058909      971901   83  Linux
/dev/sda7        58058973    61432559     1686793+  82  Linux swap / Solaris
/dev/sda8        92148903   122865119    15358108+   7  HPFS/NTFS
/dev/sda9       122865183   156280319    16707568+   b  W95 FAT32
```
```
ap@PARLE:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 30716217, Id= 7, bootable
/dev/sda2 : start= 30716280, size=125564040, Id= f
/dev/sda3 : start= 61432623, size= 30716217, Id= b
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 30716406, size= 25398639, Id=83
/dev/sda6 : start= 56115108, size=  1943802, Id=83
/dev/sda7 : start= 58058973, size=  3373587, Id=82
/dev/sda8 : start= 92148903, size= 30716217, Id= 7
/dev/sda9 : start=122865183, size= 33415137, Id= b
ap@PARLE:~$



```

---

### Post by meierfra. on 2009-04-26
To fix the partition table,  download the attached file "PT.txt" to your Ubuntu desktop and open a terminal. Rewrite your partition table via


```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```


Just as a precaution, post the output of that command. Also  copy the file
OldPT.save to a save place outside your hard drive (Flashdrive, online
storage,email account,...)

---

### Post by losher on 2009-04-26
I'm seeing someone on #ubuntu with the same problem. I think there will be more yet. Can you explain more fully what goes wrong
and how to fix it in the general case, for posterity? Thx...

---

### Post by apparle on 2009-04-26
> **meierfra. said:**
> To fix the partition table,  download the attached file "PT.txt" to your Ubuntu desktop and open a terminal. Rewrite your partition table via


```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```


Just as a precaution, post the output of that command. Also  copy the file
OldPT.save to a save place outside your hard drive (Flashdrive, online
storage,email account,...)

Could you just explain what is happening.
Also why have you shifted 
/dev/sda3 to /dev/sda8
/dev/sda8 to /dev/sda9
/dev/sda9 to /dev/sda10

Also why have you put the line twice in PT.txt??```
/dev/sda4 : start=        0, size=        0, Id= 0
```

Also If I end up messing whole of my HDD then how to fix it....considering I can't boot to live CD

---

### Post by meierfra. on 2009-04-26
> Could you just explain what is happening.
Also why have you shifted
/dev/sda3 to /dev/sda8
/dev/sda8 to /dev/sda9
/dev/sda9 to /dev/sda10

Also why have you put the line twice in PT.txt??
Somehow your partition table got messed up. This can happen for example if you partitioned your hard drive with two different partitioning  tools. Different partitioning  tools use slightly different rules for the partition tables and this can leas to confusion.  Sometimes it is already enough to install Ubuntu and then reinstall XP.


You have two problems:

> omitting empty partition (5)
This means that you have a bogus entry in your partition table. fdisk just ignores  this entry, so it does not show up in the output of "fdisk" and "sfdisk". But other programs for example "grub" do not ignore this entry and so this can cause problems booting.  


> /dev/sda2        30716280   156280319    62782020    f  W95 Ext'd (LBA)
/dev/sda3        61432623    92148839    15358108+   b  W95 FAT32The MBR has only  room to store the information of four partitions.  These four partitions are called primary partition and are numbered /dev/sda1,/dev/sda2 /dev/sda3 and /dev/sda4.

If you want to have more than four partitions, you need to have an extended partition. An extended partition is  container for  all the logical partitions.  logical partition is just a partition which is not one of the four primary partitition) The logical partition are numbered /dev/sda5, /dev/sda6, and so on.

You extended partition is /dev/sda2. It starts at sector 30716280   and ends at sector 156280319 . Inside this extended  partition you should only have logical partitions. /dev/sda3 is a primary partition (since it has a number less than 5) and starts at  sector 61432623   and ends at   92148839. So you have a primary partition inside an extended partition.

Usually this does not cause any problems. But gparted thinks the partition table is invalid and shows the whole drive as unallocated.

The easist way to fix your problem is to rwrite your partition table, so that /dev/sda3 becomes a logical partition.

So /dev/sda3 needs to have a number larger than 4..  If you look at the output of "fdisk -lu" you see that /dev/sda3 comes right after /dev/sda7. So I  moved /dev/sda3 into the /dev/sda8 spot. Of course I then had to shift /dev/sda8 and /dev/sda9 by one.


Since I changed /dev/sda3 into a logical partition, you know only have two primary partition. So you now have two empty primary partitions/dev/sda3 and /dev/sda4.

> Also If I end up messing whole of my HDD then how to fix it....considering I can't boot to live CD 

Make sure that you don't reboot before I had a look at the output of the long  "sfdisk" command. 
If things really go wrong (but I never had this happen) you will only have to find some LiveCD you can boot from, it does not have to be the Ubuntu LiveCD.
As another precaution, have a look at the partitions  with gparted before you reboot.

Are you planning to boot into Ubuntu 8.10 before you install Jaunty?
Then you should reinstall Grub after you rewrote the partition table.
If you would like help  with that, post the output of

```
sudo grub
find /boot/grub/stage2
find /grub/stage2
```

---

### Post by apparle on 2009-04-27
> So you now have two empty primary partitions/dev/sda3 and /dev/sda4.
But in the file you have posted there is no entry for /dev/sda3 and two entries for /dev/sda4
Please check the file and post the corrected file becuase others might be viewing that file.

I don't have gparted installed........but I've CLI parted installed. Will it be enough?


I am not yet sure whether I'll install jaunty right away, so I'll need 8.10 for a week at least
Will I have to modify fstab entries..........and anyother things like that
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage2
 (hd0,5)

grub> find /grub/stage2

Error 15: File not found

grub>

```

---

### Post by apparle on 2009-04-27
Also will editing the partitions affect the Windows isntallation in any way??

---

### Post by meierfra. on 2009-04-27
> /dev/sda3 and two entries for /dev/sda4
The  "/dev/sda4" is actually ignored by "sfdisk". It's just there to make the file easier to read for  humans. So  it does not matter that the file says "/dev/sda4" instead of "/dev/sda3". (But I'll will edit the file anyway, to avoid confusion)
Did you edit the file? I suggest to use my original file. sfdisk is very picky about lines breaks. For example an extra blank line will corrupt the file. 


> but I've CLI parted installed. Will it be enough?
yes. Just type "sudo parted /dev/sda print" to check on the partition table.


> Will I have to modify fstab entries..........and anyother things like that
Fstab should be using UUID. So no need to edit fstab.
But you need to edit menu.lst. (see below)

> grub> find /boot/grub/stage2
 (hd0,5)

After you wrote the partition table, you need to reinstall grub:

```
sudo grub
find /boot/grub/stage2  
root (hd0,4)
setup (hd0)
quit
```

The "find /boot/grub/stage2" is just a precaution. It should return  "(hd0,4)"

Open menu.lst via
```
gksudo gedit /boot/grub/menu.lst
```

Change 
# groot=(hd0,?)

to

#groot=(hd0,4)

Save and close the file. Go back to the terminal and type

```
sudo update-grub
```


> Also will editing the partitions affect the Windows isntallation in any way?? 
As far as I can see, it should not effect the Windows installation.

---

### Post by apparle on 2009-04-27
> Did you edit the file? I suggest to use my original file. sfdisk is very picky about lines breaks.
I was about to edit but whole HDD was at stake so I just thought I would confirm.
I will try and then post all the details

---

### Post by apparle on 2009-04-27
This the output of the long sfdisk command
```
ap@PARLE:~$ sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
[sudo] password for ap:                                                                    

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Old situation:                                            
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1911    1912-  15358108+   7  HPFS/NTFS
/dev/sda2       1912    9727    7816   62782020    f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3       3824+   5735    1912-  15358108+   b  W95 FAT32       
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4          0       -       0          0    0  Empty           
/dev/sda5       1912+   3492    1581-  12699319+  83  Linux           
                start: (c,h,s) expected (1023,254,63) found (1023,2,1)
/dev/sda6       3493+   3613     121-    971901   83  Linux           
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7       3614+   3823     210-   1686793+  82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)    
/dev/sda8       5736+   7647    1912-  15358108+   7  HPFS/NTFS           
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)    
/dev/sda9       7648+   9727    2080-  16707568+   b  W95 FAT32           
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)    
New situation:                                                            
Units = sectors of 512 bytes, counting from 0                             

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  30716279   30716217   7  HPFS/NTFS
/dev/sda2      30716280 156280319  125564040   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty          
/dev/sda4             0         -          0   0  Empty          
/dev/sda5      30716406  56115044   25398639  83  Linux          
/dev/sda6      56115108  58058909    1943802  83  Linux          
/dev/sda7      58058973  61432559    3373587  82  Linux swap / Solaris
/dev/sda8      61432623  92148839   30716217   b  W95 FAT32           
/dev/sda9      92148903 122865119   30716217   7  HPFS/NTFS           
/dev/sda10    122865183 156280319   33415137   b  W95 FAT32           
Successfully wrote the new partition table                            

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```



Now as you told this is the output of the command 'sudo parted /dev/sda print'
```
ap@PARLE:~$ sudo parted /dev/sda print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  15.7GB  15.7GB  primary   ntfs         boot
 2      15.7GB  80.0GB  64.3GB  extended               lba
 5      15.7GB  28.7GB  13.0GB  logical   ext3
 6      28.7GB  29.7GB  995MB   logical
 7      29.7GB  31.5GB  1727MB  logical   linux-swap
 8      31.5GB  47.2GB  15.7GB  logical   fat32
 9      47.2GB  62.9GB  15.7GB  logical   ntfs
10      62.9GB  80.0GB  17.1GB  logical   fat32

ap@PARLE:~$
```

It seems to me that everything is ok just the "The command to re-read the partition table failed" so I thought I should ask?

next I run
```
sudo grub
find /boot/grub/stage2  
root (hd0,4)
setup (hd0)
quit
```

when I open the /boot/grub/menu.lst file
instead of 
# groot=(hd0,?)
I found
# groot=3116095c-a5d2-4c73-8eb4-cd4cd8e8f2de

which matches the UUID of my ubuntu drive. So I didn't change anything

Next I run 
sudo update-grub

```
ap@PARLE:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ap@PARLE:~$ 
```


To me, it seems all is well but you please check and tell

---

### Post by meierfra. on 2009-04-27
> "The command to re-read the partition table failed"
That's normal. Everything looks good. Just reboot and you should be all set.

---

