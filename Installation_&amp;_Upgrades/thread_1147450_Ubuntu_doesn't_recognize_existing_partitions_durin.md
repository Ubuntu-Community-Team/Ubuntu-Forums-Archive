---
title: "Ubuntu doesn't recognize existing partitions during an install"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by psyoptic on 2009-05-03
I've noticed that there was a similar thread to this just a few days ago, but didn't know if I was having the same problem, which is a corrupted partition table. Anyways, while trying to install Ubuntu 9.04, the partition manager does not recognize my existing partition table. I am able to mount the partitions on a live CD, but the partition manager is not able to recognize them for some reason.

Here are my results for
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f804f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   453129389   226564663+   7  HPFS/NTFS
/dev/sda2       453129390   488392064    17631337+   5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       453129516   461033369     3951927   83  Linux
/dev/sda6       461033433   484488269    11727418+  83  Linux

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=453129327, Id= 7, b
/dev/sda2 : start=453129390, size= 35262675, Id= 5
/dev/sda3 : start=484488333, size=  3903732, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=453129516, size=  7903854, Id=83
/dev/sda6 : start=461033433, size= 23454837, Id=83

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.
```

Any help would be greatly appreciated!

---

### Post by psyoptic on 2009-05-03
Bump. Any suggestions?

---

### Post by caljohnsmith on 2009-05-03
> **psyoptic said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f804f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   453129389   226564663+   7  HPFS/NTFS
/dev/sda2       [COLOR="Red"]453129390   488392064[/COLOR]    17631337+   5  Extended
/dev/sda3       [COLOR="Red"]484488333   488392064[/COLOR]     1951866   82  Linux swap / Solaris
/dev/sda5       453129516   461033369     3951927   83  Linux
/dev/sda6       461033433   484488269    11727418+  83  Linux

```

Psyoptic, please be patient and observe the forum rules of not bumping your post sooner than every 24 hours. Also, it would be better if you could post a smaller screen shot rather than the large size that you did. Thanks for your understanding and cooperation. :)

Anyway, about your partition problem, unfortunately you do have a corrupt partition table at this point, and that's why the Ubuntu partitioner is not able to display your current partitions. As shown highlighted in red above, your sda3 primary partition is inside your sda2 extended partition, so sda3 should be a logical partition instead. To fix the problem, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. Then reboot, and post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
If the parted command above shows your correct partitions instead of returning an error, then the Ubuntu installer should also be able to see your current partitions. Let me know how that goes or if you run into problems.

John

---

### Post by psyoptic on 2009-05-04
Thank you for your quick response, caljohnsmith. Sorry about bumping my topic in less than 24 hours and for posting a large image. I wasn't able to find a stickied thread with the rules in it (Only one for malicious commands and another for the debate between ext3 and ext4), so I wasn't sure how long I had to wait between posts.

I've got some good news though. That new partition table you posted did the trick! After restarting and starting the installer again, Jaunty picked up my other operating systems flawlessly.

Here are the results of the commands you wanted me to try.

```
ubuntu@ubuntu:~$ sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  28205   28206- 226564663+   7  HPFS/NTFS
/dev/sda2      28206   30400    2195   17631337+   5  Extended
/dev/sda3      30158+  30400     243-   1951866   82  Linux swap / Solaris
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      28206+  28697     492-   3951927   83  Linux
/dev/sda6      28698+  30157    1460-  11727418+  83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 453129389  453129327   7  HPFS/NTFS
/dev/sda2     453129390 488392064   35262675   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     453129516 461033369    7903854  83  Linux
/dev/sda6     461033433 484488269   23454837  83  Linux
/dev/sda7     484488333 488392064    3903732  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f804f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   453129389   226564663+   7  HPFS/NTFS
/dev/sda2       453129390   488392064    17631337+   5  Extended
/dev/sda5       453129516   461033369     3951927   83  Linux
/dev/sda6       461033433   484488269    11727418+  83  Linux
/dev/sda7       484488333   488392064     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60c52a96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   156296384    78148161    7  HPFS/NTFS
```

```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA ST3250410AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  232GB  232GB   primary   ntfs         boot 
 2      232GB   250GB  18.1GB  extended                    
 5      232GB   236GB  4047MB  logical   ext3              
 6      236GB   248GB  12.0GB  logical   ext3              
 7      248GB   250GB  1999MB  logical   linux-swap
```

Thanks again for your help!

---

### Post by caljohnsmith on 2009-05-04
That's good news--glad your partition table is OK now. Cheers and have fun with your new Ubuntu install. :)

John

---

### Post by balanionut on 2009-05-05
Hello guys.

I have a similar problem with my laptop. I use Vista, Windows 7 RC and a previous Linux install. I cannot install Ubuntu 9.04 because the installer doesn't see may partitions.

they look like this:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb86566e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074088   122206454    59566183+   7  HPFS/NTFS
/dev/sda3       211270816   456213869   122471527    7  HPFS/NTFS
/dev/sda4       122206455   488392064   183092805    5  Extended
/dev/sda5       122206518   211270814    44532148+   7  HPFS/NTFS
/dev/sda6       456213933   487074734    15430401   83  Linux
/dev/sda7       487074798   488392064      658633+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```
Any advice will be appreciated. Thanks in advance!

---

### Post by caljohnsmith on 2009-05-05
> **balanionut said:**
> 
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb86566e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074088   122206454    59566183+   7  HPFS/NTFS
/dev/sda3       [COLOR="Red"]211270816   456213869[/COLOR]   122471527    7  HPFS/NTFS
/dev/sda4       [COLOR="Red"]122206455   488392064[/COLOR]   183092805    5  Extended
/dev/sda5       122206518   211270814    44532148+   7  HPFS/NTFS
/dev/sda6       456213933   487074734    15430401   83  Linux
/dev/sda7       487074798   488392064      658633+  82  Linux swap / Solaris

```

Hi Balanionut, it looks like you too have a corrupted partition table; as shown highlighted in red above, your sda3 primary partition is inside your sda4 extended partition, therefore sda3 should be a logical partition instead. If you would like help fixing your partition table, how about posting:
```
sudo sfdisk -d
```
And we can work from there.

John

---

### Post by noelrocha on 2009-05-05
Hi Guys,

I'm having the same problem. 

Follow bellow the results for:
```

 sudo fdisk -lu
 sudo sfdisk -d

```


- The "Unknown" partition is an "Mac Journaled" filesystem. 
- The "Linux" partition is an old ubuntu installation.

Results:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54494d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   126062054    63030996   83  Linux
/dev/sda2   *   126062055   318570110    96254028   af  Unknown

```


```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=126061992, Id=83
/dev/sda2 : start=126062055, size=192508056, Id=af, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

```

Thanks in advance,

Noel

---

### Post by caljohnsmith on 2009-05-05
> **noelrocha said:**
> 
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total [COLOR="Red"]312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54494d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   126062054    63030996   83  Linux
/dev/sda2   *   126062055   [COLOR="Red"]318570110[/COLOR]    96254028   af  Unknown

```

Hi Noel, your sda2 partition ends on a sector that is past the end of the drive, so that is what must be causing you problems right now. What is on that partition? I would recommend using "testdisk" to try and determine the correct ending sector for sda2 and rebuild your partition table, but it may take us a few iterations since testdisk can't read Mac Journaled file systems. To use testdisk, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your Ubuntu desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", "N" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions.

John

---

### Post by noelrocha on 2009-05-05
Hi John,

thanks for your reply. Follow bellow the results:

```

TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  7846 254 63  126061992
P HFS                   7847   0  1 19457 254 63  186530715

```

Follow the "p" :D screen of Linux partition:
```

TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   * Linux                    0   1  1  7846 254 63  126061992
Directory /

drwxr-xr-x   999   999      4096 23-May-2008 01:28 .
drwxr-xr-x   999   999      4096 23-May-2008 01:28 ..
drwx------     0     0     16384 27-Mar-2008 18:48 lost+found
drwxr-xr-x     0     0      4096 19-Mar-2008 21:38 var
drwxr-xr-x     0     0     12288  2-Dec-2008 00:05 etc
drwxr-xr-x     0     0      4096  1-Dec-2008 20:24 media
lrwxrwxrwx     0     0        11 27-Mar-2008 18:49 cdrom
drwxr-xr-x   999   999      4096 23-May-2008 01:29 bin
drwxr-xr-x     0     0      4096 24-Apr-2008 04:57 boot
drwxr-xr-x     0     0      4096 21-Apr-2008 20:38 dev
drwxr-xr-x   999   999      4096 14-May-2008 22:53 home
drwxr-xr-x     0     0      4096 19-Mar-2008 21:15 initrd
drwxr-xr-x     0     0     12288  4-May-2008 18:45 lib
drwxr-xr-x     0     0      4096  6-Feb-2008 16:47 mnt
drwxr-xr-x     0     0      4096  4-Apr-2008 19:08 opt
drwxr-xr-x     0     0      4096  6-Feb-2008 16:47 proc
drwxr-xr-x     0     0      4096 23-Sep-2008 22:01 root
drwxr-xr-x     0     0      4096 12-May-2008 02:10 sbin
drwxr-xr-x     0     0      4096 19-Mar-2008 21:15 srv
drwxr-xr-x     0     0      4096 12-Mar-2008 15:24 sys
drwxrwxrwt     0     0      4096  2-Dec-2008 00:05 tmp
drwxr-xr-x     0     0      4096 19-Mar-2008 21:17 usr
lrwxrwxrwx     0     0        33 14-Apr-2008 05:31 initrd.img
lrwxrwxrwx     0     0        30 14-Apr-2008 05:31 vmlinuz
lrwxrwxrwx     0     0        30  6-Apr-2008 15:07 vmlinuz.28774
lrwxrwxrwx     0     0        33  6-Apr-2008 15:07 initrd.img.old
lrwxrwxrwx     0     0        30  6-Apr-2008 15:07 vmlinuz.old

```


I couldn't get the "p" screen of HFS partition. Is that bad? 

Both partition exists and they work. The Linux partition is an old Ubuntu and the HFS partition is an Mac Os Leopard. I'm able to boot both of them. I'm using GRUB as boot loader.

What I'm trying to do is to install Ubuntu 9.04 in the Linux partition erasing all data. But I can't erase the Mac partition. 

Thanks again,

Noel

---

### Post by caljohnsmith on 2009-05-05
> **noelrocha said:**
> 
What I'm trying to do is to install Ubuntu 9.04 in the Linux partition erasing all data. But I can't erase the Mac partition. 

Thanks again,

Noel
So do you want to erase the Mac partition? If so, how about doing the following:
```
echo '0,0,0,-' | sudo sfdisk --no-reread -fuS /dev/sda -N2
```
Then reboot, and after that the Ubuntu installer should be able to recognize your existing sda1 linux partition. Let me know how that goes or if you run into problems.

John

---

### Post by noelrocha on 2009-05-05
> **caljohnsmith said:**
> So do you want to erase the Mac partition? If so, how about doing the following:
John

Actually, I don't want to erase the Mac partition. I want to install Ubuntu 9.04 in the old Ubuntu partition. I cannot erase the Mac partition :D


What does this command do?

Thanks again John,

Noel

---

### Post by caljohnsmith on 2009-05-05
> **noelrocha said:**
> Actually, I don't want to erase the Mac partition. I want to install Ubuntu 9.04 in the old Ubuntu partition. I cannot erase the Mac partition :D

In that case, I unfortunately can't help you any further; the forum rules state clearly that piracy and/or illegal activities will not be supported in the forums. Your Mac OS Leopard partition is obviously an illegal copy, because Apple does not support Mac OS software on PCs. I'm sorry, but the bottom line is I cannot finish helping you with your partition problem. 

John

---

### Post by balanionut on 2009-05-06
Thanks John,

Here you have:
```

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3074088, size=119132367, Id= 7, bootable
/dev/sda3 : start=211270816, size=244943054, Id= 7
/dev/sda4 : start=122206455, size=366185610, Id= 5
/dev/sda5 : start=122206518, size= 89064297, Id= 7
/dev/sda6 : start=456213933, size= 30860802, Id=83
/dev/sda7 : start=487074798, size=  1317267, Id=82

```
Can you explain the principle on how you make the txt file to rearrange the partitions?

Thank you!

---

### Post by caljohnsmith on 2009-05-06
Balanionut, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. To explain a little, here is the contents of the "partition_table.txt" file:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3074088, size=119132367, Id= 7, bootable
[COLOR="Red"]/dev/sda3 : start=        0, size=        0, Id= 0[/COLOR]
/dev/sda4 : start=122206455, size=366185610, Id= 5
/dev/sda5 : start=122206518, size= 89064297, Id= 7
[COLOR="Red"]/dev/sda6 : start=211270816, size=244943054, Id= 7[/COLOR]
/dev/sda7 : start=456213933, size= 30860802, Id=83
/dev/sda8 : start=487074798, size=  1317267, Id=82
```
So if you compare the above partition table with the one in your post #14, you will see that all I did is copy sda3 to a new logical partition after sda5, and then I renumbered the logical partitions so they have consecutive numbering. Also I deleted sda3 by making all the fields "0". It is important to note that sfdisk cannot create partition tables where the logical partitions are not in the physical order they are on the drive, so that's why I moved sda3 so that it is right after sda5 and did not put sda3 after your existing sda7 swap partition. There are other factors to consider too, but I don't want to go into all the details as it would take too much time.

So anyway, after you run the sfdisk command above, reboot to your Jaunty Live CD, and post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
If that last parted command does not return any errors and instead shows your partitions, the Jaunty installer should be able to see your partitions too, so go ahead and try installing Jaunty. Let me know how that goes or if you run into problems. :)

John

---

### Post by balanionut on 2009-05-07
John,

Thank you for helping me on this. My new table partition looks like this:

ubuntu@ubuntu:~/Desktop$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb86566e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074088   122206454    59566183+   7  HPFS/NTFS
/dev/sda4       122206455   488392064   183092805    5  Extended
/dev/sda5       122206518   211270814    44532148+   7  HPFS/NTFS
/dev/sda6       211270816   456213869   122471527    7  HPFS/NTFS
/dev/sda7       456213933   487074734    15430401   83  Linux
/dev/sda8       487074798   488392064      658633+  82  Linux swap / Solaris
ubuntu@ubuntu:~/Desktop$ sudo parted /dev/sda print
Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1574MB  1573MB  primary   ntfs              
 2      1574MB  62.6GB  61.0GB  primary   ntfs         boot 
 4      62.6GB  250GB   187GB   extended                    
 5      62.6GB  108GB   45.6GB  logical   ntfs              
 6      108GB   234GB   125GB   logical   ntfs              
 7      234GB   249GB   15.8GB  logical   ext3              
 8      249GB   250GB   674MB   logical   linux-swap

---

### Post by balanionut on 2009-05-07
John,

It worked. Now I'm posting from Ubuntu 9.04. Good job!

Thanks again!

---

### Post by caljohnsmith on 2009-05-07
Glad to hear that worked OK, balanionut. Cheers and enjoy your new 9.04 install. :)

John

---

### Post by noelrocha on 2009-05-08
Hi John,

I just would like to know how do I set the end sector of a partition.

Thanks,


Noel

---

### Post by caljohnsmith on 2009-05-08
> **noelrocha said:**
> Hi John,

I just would like to know how do I set the end sector of a partition.

Thanks,


Noel
It depends on what you are trying to do--can you give me more information? Are you trying to resize an existing partition to have a specific ending sector? Or are you trying to create a partition to have a specific ending sector? And what are the circumstances that you need to specify the exact ending sector of a partition? 

John

---

### Post by allbutnow on 2009-05-18
Hi Ubuntu Community,

I've got a laptop with Win7 RC on it. Today I spent 6 hours trying to install Ubuntu. The partition tool doesn't see any of my existing (NTFS) partitions (screenshot: [http://img404.imageshack.us/content.php?page=done&l=img404/6880/screenshotsbh.png](http://img404.imageshack.us/content.php?page=done&l=img404/6880/screenshotsbh.png)).

That's how it looks like on Win7: [http://img527.imageshack.us/img527/5286/captureo.png](http://img527.imageshack.us/img527/5286/captureo.png)

After many researches I found this thread. It seems that you guys found out how to resolve this issue. From what I understand, I have to give you the output of some console commands.

Could you please help me? Thanks in advance.

```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
gives the following:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6846516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   163842047    81817600    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       163842048   409602047   122880000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
ubuntu@ubuntu:~$ sudo sfdisk -d

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   204800, Id= 7, bootable
/dev/sda2 : start=   206848, size=163635200, Id= 7
/dev/sda3 : start=163842048, size=245760000, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?  i'm not sure :D

```

---

### Post by allbutnow on 2009-05-20
I still can't install any Linux without formatting whole disk... Any help would be appreciated.

thanks in advance

---

### Post by owkaye on 2009-05-29
Hello everyone,

I've experienced the same (or a similar) problem as psyoptic with what appears to be a corrupted partition table, so I hope I'm not out of line by adding to this thread instead of starting a new one.  

Here is the information I collected in an attempt to diagnose the problem:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6c759d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2         3662820    90847574    43592377+   7  HPFS/NTFS
/dev/sda3   *   295649280   312580095     8465408   17  Hidden HPFS/NTFS
/dev/sda4         3084480   295644194   146279857+   5  Extended
/dev/sda5         3084543     3662819      289138+  82  Linux swap / Solaris
/dev/sda6        90847638   254678444    81915403+  83  Linux
/dev/sda7       254678508   295644194    20482843+   b  W95 FAT32

Partition table entries are not in disk order


ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3662820, size= 87184755, Id= 7
/dev/sda3 : start=295649280, size= 16930816, Id=17, bootable
/dev/sda4 : start=  3084480, size=292559715, Id= 5
/dev/sda5 : start=  3084543, size=   578277, Id=82
/dev/sda6 : start= 90847638, size=163830807, Id=83
/dev/sda7 : start=254678508, size= 40965687, Id= b


ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.
```My guess is that I'm going to need to install a new partition table like psyoptic did after caljohnsmith gave him a new one.  Unfortunately I don't know how to create a valid partition table, which leads me to this request:

Caljohnsmith, can you possibly create a new partition table for me so I can install it and run the same tests and procedures as psyoptic did?  Thanks in advance if you can help me with this!  :)

It seems I may have a problem psyoptic did not have, too:  

Partition 1 does not end on a cylinder boundary.  Given the fact that the next partition does not begin at the end of Partition1, can this be fixed simply by adjusting the size of Partition 1 in the new partition table?  Or is my thinking incorrect here?

Thanks for any help.

---

### Post by Gilles92 on 2009-05-29
Hello everyone,

I'm trying to install Ubuntu 9.04 on my IBM laptop currently running WinXP but the installer doesn't see the the 3 existing partitions.

Below is the information I collected :
sda1 is my windows partition that I want to replace by Ubuntu.
sda3 and sda5 are NTSF partition with my data that I want to keep.

```
sudo fdisk -l

Disque /dev/sda: 250.0 Go, 250059350016 octets
240 têtes, 63 secteurs/piste, 32301 cylindres
Unités = cylindres de 15120 * 512 = 7741440 octets
Identifiant de disque : 0x071f071e

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        1084     8195008+   7  HPFS/NTFS
/dev/sda2            1085       17753   126017640    f  W95 Etendue (LBA)
/dev/sda3           17754       32302   109988077+   7  HPFS/NTFS
/dev/sda5            1085       17753   126017608+   7  HPFS/NTFS
```also

```
ubuntu@ubuntu:~$ sudo sfdisk -d
Attention : la partition étendue ne débute pas sur une frontière de.
cylindres. DOS et Linux interpréteront les contenus différemment.
# table de partitions de /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 16390017, Id= 7, bootable
/dev/sda2 : start= 16390080, size=252035280, Id= f
/dev/sda3 : start=268430085, size=219976155, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 16390143, size=252035217, Id= 7
ubuntu@ubuntu:~$ sudo sfdisk -l

Disque /dev/sda : 30401 cylindres, 255 têtes, 63 secteurs/piste
Attention : la partition étendue ne débute pas sur une frontière de.
cylindres. DOS et Linux interpréteront les contenus différemment.
Attention : la table de partitions semble avoir été créée
  pour C/H/S=*/240/63 (au lieu de 30401/255/63).
Pour ce rapport, cette géométrie sera supposée telle.
Unités= cylindres de 7741440 octets, blocs de 1024 octets, décompte à partir de 0

   Périph Amor Début     Fin   #cyls    #blocs    Id  Système
/dev/sda1   *      0+   1083    1084-   8195008+   7  HPFS/NTFS
/dev/sda2       1084   17752   16669  126017640    f  W95 Etendue (LBA)
                début: (c,h,s) attendu (1023,239,63) trouvé (1023,0,1)
/dev/sda3      17753+  32301   14549- 109988077+   7  HPFS/NTFS
                début: (c,h,s) attendu (1023,239,63) trouvé (1023,75,1)
/dev/sda4          0       -       0          0    0  Vide
/dev/sda5       1084+  17752   16669- 126017608+   7  HPFS/NTFS
                début: (c,h,s) attendu (1023,239,63) trouvé (1023,1,1)
```(sorry it's in french), it says that the extended partition doesn't start on the cylinder boundary... and I don't know how to fix this...


Any help would be greatly appreciated.

---

### Post by Gilles92 on 2009-06-01
Hi CalJohnSmith, 

Is it possible to fix my partition table like you did for Balanionut or do I have to format the whole disk ?

Gilles92

---

### Post by manox on 2009-10-22
Hi I'm having same problem my disk is showed as 1 partition in ubuntu installer 
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750   312576704   135805477+   f  W95 Ext'd (LBA)
/dev/sda3        53255538   293041664   119893063+   7  HPFS/NTFS
/dev/sda5        40965876    46042289     2538207   82  Linux swap / Solaris
/dev/sda6        46058418    53255474     3598528+  83  Linux
/dev/sda7       293041728   312576704     9767488+  83  Linux

```

---

### Post by Domukuan on 2009-10-23
I am also having the same problem. Here's the code I could get:

```
ubuntu@ubuntu:~$ sudo sfdisk -d

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=209717185, Id=42
/dev/sda2 : start=209717248, size= 52428800, Id=42
/dev/sda3 : start=262146048, size=1691377072, Id=42
/dev/sda4 : start=        0, size=        0, Id= 0

```sudo sfdisk -lu gave this: 

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x496a4200

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   209717247   104858592+  42  SFS
/dev/sda2       209717248   262146047    26214400   42  SFS
/dev/sda3       262146048  1953523119   845688536   42  SFS

```

Don't really know how to read this though... any help is greatly appreciated.

---

### Post by iapelaezf69 on 2009-10-25
Hi everybody,

I'm having the same problem as the guy with the two partitions that end with the same number. I haven't seen any more replies from John though.

Is anybody there willing to help me? I'd appreciate it!

Cheers,

Ivan

---

### Post by manox on 2009-10-26
I actually have dual boot with XP and I have tried to install Partition magic on xp which has fixed partitions issues and the Ubuntu hasn't got any problem to find all partitions

---

### Post by jchstevens on 2009-10-27
I've been having similar problems to those being posted in this thread whilst trying to install 9.04 on my Dell Inspiron 6400. 

I've reduced the size of my Vista partition and tried to keep the other Dell partitions intact.  After losing my MBR and struggling to recover it with testdisk, I eventually ended up with partitions that work for Vista and can be seen and mounted by the live Ubuntu CD.  However, when I try to install Ubuntu to the free space on my disk(/dev/sda4), it sees the whole disk as being unpartitioned.

Please could someone take a look at the following output and give me some advice:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   *      161792    21133311    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3        21133312   174987240    76926964+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4       174996045   312592769    68798362+   f  W95 Ext'd (LBA)
/dev/sda5       308385792   312578047     2096128    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   160587, Id=de
/dev/sda2 : start=   161792, size= 20971520, Id= 7, bootable
/dev/sda3 : start= 21133312, size=153853929, Id= 7
/dev/sda4 : start=174996045, size=137596725, Id= f
/dev/sda5 : start=308385792, size=  4192256, Id= c

```

Thanks very much.

---

### Post by cool_viju77 on 2009-12-24
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52420094    26210016    7  HPFS/NTFS
/dev/sda2        52420095   234436544    91008225    5  Extended
/dev/sda3       114366739   155975084    20804173    7  HPFS/NTFS
/dev/sda5        52420162   114366734    30973286+   7  HPFS/NTFS
/dev/sda6       155975155   229841954    36933400    7  HPFS/NTFS
/dev/sda7       229842018   234436544     2297263+  82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043284480 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897040 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128     7896959     3948416    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 143, 36)
[CENTER]
[/CENTER]
 



ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 52420032, Id= 7, bootable
/dev/sda2 : start= 52420095, size=182016450, Id= 5
/dev/sda3 : start=114366739, size= 41608346, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 52420162, size= 61946573, Id= 7
/dev/sda6 : start=155975155, size= 73866800, Id= 7
/dev/sda7 : start=229842018, size=  4594527, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=      128, size=  7896832, Id= b, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

ANY SUGGESTIONS FOR THIS ONE.....
THANKX......

---

