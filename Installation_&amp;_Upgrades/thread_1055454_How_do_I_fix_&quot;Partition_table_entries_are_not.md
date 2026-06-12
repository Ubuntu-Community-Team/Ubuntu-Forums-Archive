---
title: "How do I fix &quot;Partition table entries are not in disk order&quot; error?"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Ray Hamilton on 2009-01-30
Hi 

I am trying to install Ubuntu 7.10 and eventually 8.04, but the installer does not see the existing partitions. fdisk -l gives me the message "Partition table entries are not in disk order".  I know this is the problem but even after reading through the forums entries, I do not know how to fix this. I am sure this must be a fairly common problem.

---

### Post by jrusso2 on 2009-01-30
I don't know I have never seen this error.  Usually it has to do with over lapping partitions.

I would delete all the partitions, you will lose your data and make new ones if this possible for you to do.

Seems like this happens when you resize partitions.

---

### Post by caljohnsmith on 2009-01-30
It's OK if the partitions are not in the same order as they are physically on the HDD, but the question is if your partition table is corrupt. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by Ray Hamilton on 2009-02-02
Sorry for the delay in posting. here is the output requested

sudo fdisk -lu
Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/hda2        68675040    78140159     4732560   83  Linux
/dev/hda3        39070080    48516299     4723110   83  Linux
/dev/hda4        48516426    68661809    10072692    5  Extended
/dev/hda5        67392738    68661809      634536   82  Linux swap / Solaris
/dev/hda6        53143146    66734009     6795432   83  Linux
/dev/hda7        66734073    67392674      329301   82  Linux swap / Solaris
/dev/hda8   *    48516426    52869914     2176744+  83  Linux
/dev/hda9        52869978    53143019      136521   82  Linux swap / Solaris

Partition table entries are not in disk order

sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/hda
unit: sectors

/dev/hda1 : start=       63, size= 39070017, Id= 7, bootable
/dev/hda2 : start= 68675040, size=  9465120, Id=83
/dev/hda3 : start= 39070080, size=  9446220, Id=83
/dev/hda4 : start= 48516426, size= 20145384, Id= 5
/dev/hda5 : start= 67392738, size=  1269072, Id=82
/dev/hda6 : start= 53143146, size= 13590864, Id=83
/dev/hda7 : start= 66734073, size=   658602, Id=82
/dev/hda8 : start= 48516426, size=  4353489, Id=83, bootable
/dev/hda9 : start= 52869978, size=   273042, Id=82

I hope this will help us get to the bottom of the problem.

---

### Post by caljohnsmith on 2009-02-02
> **Ray Hamilton said:**
> 
```
sudo fdisk -lu
Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/hda2        68675040    78140159     4732560   83  Linux
/dev/hda3        39070080    48516299     4723110   83  Linux
/dev/[COLOR="Red"]hda4        48516426[/COLOR]    68661809    10072692    5  Extended
/dev/hda5        67392738    68661809      634536   82  Linux swap / Solaris
/dev/hda6        53143146    66734009     6795432   83  Linux
/dev/hda7        66734073    67392674      329301   82  Linux swap / Solaris
/dev/[COLOR="Red"]hda8   *    48516426[/COLOR]    52869914     2176744+  83  Linux
/dev/hda9        52869978    53143019      136521   82  Linux swap / Solaris
```

It looks like the problem is that your hda8 linux logical partition starts on the exact same sector as the hda4 extended partition; hda8 can start on any sector after the start of hda4 (and usually hda8 would start at least 63 sectors beyond the starting sector of hda4), so your partition table is corrupt at this point. How about first seeing if you can mount hda8:
```
sudo mount /dev/hda8 /mnt && ls -l /mnt
```
If that gives you a directory listing of hda8, then it is obvious that hda8 has the correct starting sector, and the problem is with your hda4 extended partition starting sector. So if you can see hda8's root directory with the above command, next do:
```
echo "48516300,20145510,5" | sudo sfdisk --no-reread -fuS /dev/hda -N4 -O ~/Desktop/hda_sectors_modified.save
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, please copy that file to a different drive, or you could for instance save it to your email account or something like that. After that, reboot, and please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/hda print
```
And also I just wanted to mention, your multiple linux installs can share the same swap partition, so there is really no need to have three swap partitions. If you would like some help configuring your distros so they all use the same swap partition, let me know. Then you could delete two of your swap partitions and use that space as you please. Let me know if you are interested.

---

### Post by Ray Hamilton on 2009-02-03
Here is the output of the first command:
Disk /dev/hda: 77520 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/hda1   *        63  39070079   39070017   7  HPFS/NTFS
/dev/hda2      68675040  78140159    9465120  83  Linux
/dev/hda3      39070080  48516299    9446220  83  Linux
/dev/hda4      48516426  68661809   20145384   5  Extended
/dev/hda5      67392738  68661809    1269072  82  Linux swap / Solaris
/dev/hda6      53143146  66734009   13590864  83  Linux
/dev/hda7      66734073  67392674     658602  82  Linux swap / Solaris
/dev/hda8   *  48516426  52869914    4353489  83  Linux
/dev/hda9      52869978  53143019     273042  82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/hda1   *        63  39070079   39070017   7  HPFS/NTFS
/dev/hda2      68675040  78140159    9465120  83  Linux
/dev/hda3      39070080  48516299    9446220  83  Linux
/dev/hda4      48516300  68661809   20145510   5  Extended
/dev/hda5      67392738  68661809    1269072  82  Linux swap / Solaris
/dev/hda6      53143146  66734009   13590864  83  Linux
/dev/hda7      66734073  67392674     658602  82  Linux swap / Solaris
/dev/hda8   *  48516426  52869914    4353489  83  Linux
/dev/hda9      52869978  53143019     273042  82  Linux swap / Solaris
Warning: partition 3 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

---

### Post by Ray Hamilton on 2009-02-03
After the above post GRUB was stuffed - cannot load stage 1.5
Currently I am using a SUPERGRUB CD that managed to find a Windows partition.  (I suspect the PCLinuxOS as causing some of the problems becuase grub has never been able to use it since I tried to install it last year!)  What now?  Especially in view of the fact that I didn't take a copy of the file - hopefully I'll be able to "recover" this shortly.

---

### Post by caljohnsmith on 2009-02-03
You never mentioned, but were you able to successfully mount hda8 and view its root directory? To try and restore Grub, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return the partitions that have Grub's boot files in the form of (hdX,Y) where X and Y are numbers, for example (hd0,5), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands.

---

### Post by Ray Hamilton on 2009-02-03
Yes, sorry, hda8 mounted and I was able to see the directory, that is why I went ahead with the fix of the partition table.

I am going to try fixing grub.

---

### Post by Ray Hamilton on 2009-02-04
I have tried the grub thing (actually using SuperGrub Disk) and I only have a non-working Linux partition, a Swap, a Windows and another with only lost+found.  I also cannot seem to get my LiveCD to set up wireless!! I am currently using my Windows partition. HEEEELLPP!!

---

### Post by caljohnsmith on 2009-02-04
If you want help, how about giving more details of the problem and what your goal is. What happened when you tried the commands I gave? Did you get any errors? What do you mean by "one non-working linux partition"? What about the other three partitions--can you mount them and access them? Did you look in the lost+found folder of the one partition to see if it has any of your files? Can you mount your linux partitions from the Live CD and and then save your important files to some other drive or maybe to your Windows partition? If you can do that then you could at least reinstall.

---

### Post by Ray Hamilton on 2009-02-05
My goal is to put the partitions back as they were if possible, to double check if there was anything important I need to keep.  Then put things into such an order that I can install Ubuntu 7.10 to learn as much as I can from a book I have about Ubuntu 7.10)

Here are the results of the last 3 commands you asked me to enter 

ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 6
Warning: invalid flag 0x83d0 of partition table 6 will be corrected by w(rite)

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        68675040    78140159     4732560   83  Linux
/dev/sda3        39070080    48516299     4723110   83  Linux
/dev/sda4        48516300    68661809    10072755    5  Extended
/dev/sda5        67392612    68661683      634536   82  Linux swap / Solaris
/dev/sda6   ?  1814276593  1814277213         310+  ff  BBT

Partition table entries are not in disk order

Disk /dev/sdb: 65 MB, 65454080 bytes
4 heads, 32 sectors/track, 998 cylinders, total 127840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef2a8f94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32      127839       63904    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 3, 32) logical=(998, 2, 32)

ubuntu@ubuntu:~$ sudo sfdisk -d

sfdisk: ERROR: sector 53142894 does not have an msdos signature
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id= 7, bootable
/dev/sda2 : start= 68675040, size=  9465120, Id=83
/dev/sda3 : start= 39070080, size=  9446220, Id=83
/dev/sda4 : start= 48516300, size= 20145510, Id= 5
/dev/sda5 : start= 67392612, size=  1269072, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       32, size=   127808, Id= 6, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
ubuntu@ubuntu:~$ sudo parted /dev/hda print
Error: Could not stat device /dev/hda - No such file or directory.        
Retry/Cancel? r                                                           
Error: Could not stat device /dev/hda - No such file or directory.        
Retry/Cancel?

---

### Post by caljohnsmith on 2009-02-08
OK, how about first doing:
```
sudo fdisk -lu
```
See if your drive is sda or hda, then do:
```
sudo fdisk /dev/sda
```
But replace sda with hda if necessary. At the fdisk prompt type "w" and enter. Next post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print

```
Replace sda with hda above if necessary.

---

### Post by Ray Hamilton on 2009-02-10
Here are the results of the commands you asked me to enter, after sudo fdisk/dev/sda and pressing enter at the prompt:

The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 6

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        68675040    78140159     4732560   83  Linux
/dev/sda3        39070080    48516299     4723110   83  Linux
/dev/sda4        48516300    68661809    10072755    5  Extended
/dev/sda5        67392612    68661683      634536   82  Linux swap / Solaris
/dev/sda6   ?  1814276593  1814277213         310+  ff  BBT

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id= 7, bootable
/dev/sda2 : start= 68675040, size=  9465120, Id=83
/dev/sda3 : start= 39070080, size=  9446220, Id=83
/dev/sda4 : start= 48516300, size= 20145510, Id= 5
/dev/sda5 : start= 67392612, size=  1269072, Id=82
/dev/sda6 : start=1814276593, size=      621, Id=ff
/dev/sda7 : start=2011916942, size=4173628185, Id=ff
/dev/sda8 : start=2264655070, size=3229946052, Id= 0
/dev/sda9 : start=1499287654, size=4285548171, Id= 0
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!                           
Information: Don't forget to update /etc/fstab, if necessary.

---

### Post by Ray Hamilton on 2009-02-10
Here are the results of the commands you asked me to enter, after sudo fdisk/dev/sda and pressing enter at the prompt:

The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 6

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        68675040    78140159     4732560   83  Linux
/dev/sda3        39070080    48516299     4723110   83  Linux
/dev/sda4        48516300    68661809    10072755    5  Extended
/dev/sda5        67392612    68661683      634536   82  Linux swap / Solaris
/dev/sda6   ?  1814276593  1814277213         310+  ff  BBT

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id= 7, bootable
/dev/sda2 : start= 68675040, size=  9465120, Id=83
/dev/sda3 : start= 39070080, size=  9446220, Id=83
/dev/sda4 : start= 48516300, size= 20145510, Id= 5
/dev/sda5 : start= 67392612, size=  1269072, Id=82
/dev/sda6 : start=1814276593, size=      621, Id=ff
/dev/sda7 : start=2011916942, size=4173628185, Id=ff
/dev/sda8 : start=2264655070, size=3229946052, Id= 0
/dev/sda9 : start=1499287654, size=4285548171, Id= 0
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!                           
Information: Don't forget to update /etc/fstab, if necessary.

---

### Post by caljohnsmith on 2009-02-10
OK, how about instead doing:
```
sudo fdisk /dev/sda
```
This time press "d", then "6" for the partition, then "w" to write the changes. Then post the output again of:
```
sudo fdisk -lu
```

---

### Post by Ray Hamilton on 2009-02-10
Hi caljohnsmith

The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 5

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        68675040    78140159     4732560   83  Linux
/dev/sda3        39070080    48516299     4723110   83  Linux
/dev/sda4        48516300    68661809    10072755    5  Extended
/dev/sda5        67392612    68661683      634536   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-02-11
OK, let's try doing this differently, so first do:
```
sudo fdisk -lu
```
Make sure your HDD is still listed as sda, and if so, proceed by downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. Next reboot your Live CD, and post the new output of:
```
sudo fdisk -lu; sudo sfdisk -d; sudo parted /dev/sda print
```

---

### Post by Ray Hamilton on 2009-02-12
Hi caljohnsmith, here is the output of the first set of commands

ubuntu@ubuntu:~$ sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt

Disk /dev/sda: 4864 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2431    2432-  19535008+   7  HPFS/NTFS
                end: (c,h,s) expected (1023,254,63) found (1023,15,63)
/dev/sda2       4274+   4863     590-   4732560   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,15,63)
                end: (c,h,s) expected (1023,254,63) found (1023,15,63)
/dev/sda3       2432    3019     588    4723110   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,15,63)
                end: (c,h,s) expected (1023,254,63) found (1023,15,63)
/dev/sda4       3020    4273    1254   10072755    5  Extended
                start: (c,h,s) expected (1023,254,63) found (1023,15,63)
                end: (c,h,s) expected (1023,254,63) found (1023,15,63)
/dev/sda5       4194+   4273-     79-    634536   82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,15,63)
                end: (c,h,s) expected (1023,254,63) found (1023,15,63)
/dev/sda6   ? 124948+ 117395- 259797- 2086814092+  ff  BBT
                start: (c,h,s) expected (1023,254,63) found (368,139,3)
                end: (c,h,s) expected (1023,254,63) found (708,208,3)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  39070079   39070017   7  HPFS/NTFS
/dev/sda2      68675040  78140159    9465120  83  Linux
/dev/sda3      39070080  48516299    9446220  83  Linux
/dev/sda4      48516300  68661809   20145510   5  Extended
/dev/sda5      48516426  52869914    4353489  83  Linux
/dev/sda6      52869978  53143019     273042  82  Linux swap / Solaris
/dev/sda7      53143146  66734009   13590864  83  Linux
Warning: partition 2 does not start at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

---

### Post by Ray Hamilton on 2009-02-12
Hi caljohnsmith, here is the output from the second command "list":

ubuntu@ubuntu:~$ sudo fdisk -lu; sudo sfdisk -d; sudo parted /dev/sda print

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        68675040    78140159     4732560   83  Linux
/dev/sda3        39070080    48516299     4723110   83  Linux
/dev/sda4        48516300    68661809    10072755    5  Extended
/dev/sda5        48516426    52869914     2176744+  83  Linux
/dev/sda6        52869978    53143019      136521   82  Linux swap / Solaris
/dev/sda7        53143146    66734009     6795432   83  Linux

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id= 7, bootable
/dev/sda2 : start= 68675040, size=  9465120, Id=83
/dev/sda3 : start= 39070080, size=  9446220, Id=83
/dev/sda4 : start= 48516300, size= 20145510, Id= 5
/dev/sda5 : start= 48516426, size=  4353489, Id=83
/dev/sda6 : start= 52869978, size=   273042, Id=82
/dev/sda7 : start= 53143146, size= 13590864, Id=83

Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  20.0GB  20.0GB  primary   ntfs         boot 
 3      20.0GB  24.8GB  4836MB  primary   ext3              
 4      24.8GB  35.2GB  10.3GB  extended                    
 5      24.8GB  27.1GB  2229MB  logical   ext3              
 6      27.1GB  27.2GB  140MB   logical   linux-swap        
 7      27.2GB  34.2GB  6959MB  logical   ext3              
 2      35.2GB  40.0GB  4846MB  primary   ext3              

Information: Don't forget to update /etc/fstab, if necessary.

---

### Post by caljohnsmith on 2009-02-12
It looks like your partition table is fine now according to the results you posted. In case you hadn't all ready noticed, we rearranged your partitions to be in the same order as they are physically on the HDD (even though that's not necessary, it was convenient to do so), and also we deleted your two extra swap partitions. So you should be able to go ahead and install Ubuntu to either of those linux partitions, or you should be able to use gparted now to make whatever partition changes you want. Good luck with your Ubuntu install.

---

### Post by Ray Hamilton on 2009-02-14
Hi caljohnsmith

I am posting this from my newly installed ubuntu 7.10 (only had a few problems!), I think everything is okay with my existing partitions.

Thanks, you have very helpful and knowledgeable. I hope I can make some contribution back to the community with the knowledge I gain.

Ray Hamilton

---

