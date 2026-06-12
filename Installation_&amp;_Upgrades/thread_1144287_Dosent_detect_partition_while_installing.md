---
title: "Dosent detect partition while installing"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by bonzi on 2009-04-30
I am trying to install ubuntu 9.04 in my machine. When I take manual partition option it dosent detect the existing partitions. But when I boot into the live cd all the partitions are shown in 'Places' ie I can mount all the drives. I have 2 NTFS and a ext3 partition which was used by ubuntu 8.04. [I must also mention I had screwed up the boot loader and currently it dosent have one]. What do you think is the reason? Any help is appreciated.

---

### Post by caljohnsmith on 2009-04-30
If your HDD has a slightly corrupt partition table, sometimes you can still mount and read the partitions OK, yet gparted or the Ubuntu installer will choke and not show any partitions since the partition table needs to be fixed. To check if that might be your problem, how about opening a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
We can work from there if you want.

John

---

### Post by bonzi on 2009-04-30
Thanks john for the reply. Heres the output.
```

sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   200648519   100324228+   7  HPFS/NTFS
/dev/sda2       200648704   292808703    46080000    7  HPFS/NTFS
/dev/sda3       292816755   296800858     1992052   82  Linux swap / Solaris
/dev/sda4       296800859   312592769     7895955+   f  W95 Ext'd (LBA)
/dev/sda5       296800875   312576698     7887912   83  Linux

ubuntu@ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=200648457, Id= 7, bootable
/dev/sda2 : start=200648704, size= 92160000, Id= 7
/dev/sda3 : start=292816755, size=  3984104, Id=82
/dev/sda4 : start=296800859, size= 15791911, Id= f
/dev/sda5 : start=296800875, size= 15775824, Id=83

ubuntu@ubuntu:~$ sudo parted /dev/sda1 print
Model: Unknown (unknown)
Disk /dev/sda1: 103GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  103GB  103GB  ntfs              

ubuntu@ubuntu:~$ sudo parted /dev/sda2 print
Model: Unknown (unknown)
Disk /dev/sda2: 47.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  47.2GB  47.2GB  ntfs              

ubuntu@ubuntu:~$ sudo parted /dev/sda3 print
Error: /dev/sda3: unrecognised disk label                                 
ubuntu@ubuntu:~$ sudo parted /dev/sda4 print
Error: Can't have a partition outside the disk!                           
ubuntu@ubuntu:~$ sudo parted /dev/sda5 print
Model: Unknown (unknown)
Disk /dev/sda5: 8077MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags

```


Hope you can help me with  info.

---

### Post by caljohnsmith on 2009-05-01
> **bonzi said:**
> Thanks john for the reply. Heres the output.
```

sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total [COLOR="Red"]312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   200648519   100324228+   7  HPFS/NTFS
/dev/sda2       200648704   292808703    46080000    7  HPFS/NTFS
/dev/sda3       292816755   296800858     1992052   82  Linux swap / Solaris
/dev/sda4       296800859   [COLOR="Red"]312592769[/COLOR]     7895955+   f  W95 Ext'd (LBA)
/dev/sda5       296800875   312576698     7887912   83  Linux

```
Unfortunately, as I suspected, your partition table is slightly corrupt; as shown highlighted in red, your sda4 extended partition's ending sector exceeds the total sectors available on the HDD. But in a way that's good news, because if that is the only problem, it should be easy to fix. So how about doing:
```
echo "296800859,15775840,f" | sudo sfdisk --no-reread -fuS /dev/sda -N4
```
After that reboot your Live CD, and then once you are back in Ubuntu post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
Please note that it is "sda" in the parted command above, not sda1, sda2, etc. If the parted command does not return any errors and shows your partitions, you should be able to install Ubuntu using the manual partitioning option. Let me know how it goes or if you run into problems.

Cheers,
John

---

### Post by bonzi on 2009-05-01
Thanks again John. Unfortunately it still shows an error. :(

```

ubuntu@ubuntu:~$ echo "296800859,15775840,f" | sudo sfdisk --no-reread -fuS /dev/sda -N4

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 200651849  200651787   7  HPFS/NTFS
/dev/sda2     200648704 292816754   92168051   7  HPFS/NTFS
/dev/sda3     292816755 296800858    3984104  82  Linux swap / Solaris
/dev/sda4     296800859 312592769   15791911   f  W95 Ext'd (LBA)
/dev/sda5     296800875 312576698   15775824  83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 200651849  200651787   7  HPFS/NTFS
/dev/sda2     200648704 292816754   92168051   7  HPFS/NTFS
/dev/sda3     292816755 296800858    3984104  82  Linux swap / Solaris
/dev/sda4     296800859 312576698   15775840   f  W95 Ext'd (LBA)
/dev/sda5     296800875 312576698   15775824  83  Linux
Warning: partitions 1 and 2 overlap
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)


```

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26962695

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   200651849   100325893+   7  HPFS/NTFS
/dev/sda2       200648704   292816754    46084025+   7  HPFS/NTFS
/dev/sda3       292816755   296800858     1992052   82  Linux swap / Solaris
/dev/sda4       296800859   312576698     7887920    f  W95 Ext'd (LBA)
/dev/sda5       296800875   312576698     7887912   83  Linux
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                           


```

---

### Post by caljohnsmith on 2009-05-01
> **bonzi said:**
> 
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26962695

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   [COLOR="Red"]200651849[/COLOR]   100325893+   7  HPFS/NTFS
/dev/sda2       [COLOR="Red"]200648704[/COLOR]   292816754    46084025+   7  HPFS/NTFS
/dev/sda3       292816755   296800858     1992052   82  Linux swap / Solaris
/dev/sda4       296800859   312576698     7887920    f  W95 Ext'd (LBA)
/dev/sda5       296800875   312576698     7887912   83  Linux
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                           

```
So the problem with your sda4 extended partition exceeding the end of the HDD is fixed, but unfortunately I overlooked the fact that your sda2 partition starts at a sector before the ending sector of sda1; thus those partitions overlap. At this point I would recommend using "testdisk" to find the correct start/stop sectors for your sda1 and sda2 partitions; how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your Ubuntu desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there. :)

John

---

### Post by meierfra. on 2009-05-01
> I overlooked the fact that your sda2 partition starts at a sector before the ending sector of sda1;

**John:** You did not overlook it. The end point of /dev/sda1 has changed from post 3 to post 5:


```

/dev/sda1   *          63   [COLOR="Red"]200648519 [/COLOR]  100324228+   7  HPFS/NTFS
/dev/sda1   *          63   [COLOR="Red"]200651849[/COLOR]   100325893+   7  HPFS/NTFS

```

Looks like a bug in sfdisk to me. (edit:  I'm withdrawing this statement.  See next two posts)

---

### Post by bonzi on 2009-05-01
No probably its not a bug. I had tried running chkdsk from windows. That might have changed something. I will post the result of testdisk asap.

---

### Post by caljohnsmith on 2009-05-01
> **meierfra. said:**
> **John:** You did not overlook it. The end point of /dev/sda1 has changed from post 3 to post 5:


```

/dev/sda1   *          63   [COLOR="Red"]200648519 [/COLOR]  100324228+   7  HPFS/NTFS
/dev/sda1   *          63   [COLOR="Red"]200651849[/COLOR]   100325893+   7  HPFS/NTFS

```

Looks like a bug in sfdisk to me.
Thanks so much for catching that, meierfra, I wasn't paying close enough attention. :) I'm curious what you think about the fact that when bonzi ran the sfdisk command to resize sda4, the first partition listing that sfdisk gave shows sda1 and sda2 overlapping; I was under the impression that the first partition listing sfdisk gives happens before sfdisk does anything, and once sfdisk does the requested operation, then the change is shown in the next partition listing that sfdisk gives. If that is true (please correct me if I'm wrong), then that would mean it's not sfdisk's fault that sda1 has a different ending sector and thus overlaps sda2; something else must have changed it in the time between bonzi's two posts. I would doubt running chkdsk on the partition would change its ending sector since I've never heard of that happening to anyone else before, but what do you think? And bonzi, can you think of anything else you did that might have changed sda1's ending sector?

John

---

### Post by bonzi on 2009-05-01
[LEFT]Heres the output for TestDisk

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 12489 202  9  200648457
D HPFS - NTFS              0  53 55 12489 254 63  200648457
D HPFS - NTFS          12489 205  5 18226 127 13   92160000 [New Volume]
* Linux Swap           18227   0  1 18474 254 47    3984104
P Linux                18475   0  1 19456 254 57   15775824


```

I tried using system rescue cd (and another recovery tool). Probably that could have changed it.

I couldnt list the files in 
D HPFS - NTFS              0  53 55 12489 254 63  200648457 that was recovered after deepscan but had no problems in listing the rest.
[/LEFT]

---

### Post by caljohnsmith on 2009-05-01
> **bonzi said:**
> Heres the output for TestDisk

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1 12489 202  9  200648457
[COLOR="Red"]D[/COLOR] HPFS - NTFS              0  53 55 12489 254 63  200648457
[COLOR="Red"]P[/COLOR] HPFS - NTFS          12489 205  5 18226 127 13   92160000 [New Volume]
[COLOR="Red"]P[/COLOR] Linux Swap           18227   0  1 18474 254 47    3984104
[COLOR="Red"]L[/COLOR] Linux                18475   0  1 19456 254 57   15775824


```

OK, how about using your up/down arrow keys to select each partition shown above, and then mark each partition as shown highlighted in red  using your right/left arrow keys. Once you are sure all the partitions are marked exactly as shown above, press enter to get the next screen, and then choose the option to write the new partition table. After that exit testdisk, reboot the Live CD, and please post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
And if the parted command doesn't return any errors, go ahead and try installing Ubuntu. Let us know how it goes or if you run into problems again. 

John

---

### Post by bonzi on 2009-05-02
Nope still no luck.

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total[COLOR=Red] 312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   200648519   100324228+   7  HPFS/NTFS
/dev/sda2       200648704   292808703    46080000    7  HPFS/NTFS
/dev/sda3       292816755   296800858     1992052   82  Linux swap / Solaris
/dev/sda4       296800859   [COLOR=Red]312592769[/COLOR]     7895955+   f  W95 Ext'd (LBA)
/dev/sda5       296800875   312576698     7887912   83  Linux
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!     

```

Can I solve the prob by removing the ext3 partition?

---

### Post by charliko on 2009-05-02
Hi    I read this thread with great interest.  I know that my partition tables are corrupt.  I also know that I would like to simply wipe the disks and start over with Ubuntu and Vista.  I have tried to wipe and rewipe.  Still can run Windows if i leave the install disk in the optical drive, but then use Wubi to start Ubuntu.  While I wait for some code solutions to the Belkin USB and 9.4 wifi issues (being connected to my access point but not the internet as well as encryption confusion on my part), I would like to get things right with these two hard drives.

Regarding the hard drives with all the corrupted partition tables, as well as the inability to read iso's on the optical drive at boot up, am i doomed to just buy new hard drives to set things up correctly??  I have a feeling the answer is yes, buy new hard drives.  

Thanks in advance for any input.

-Charlie......my original project to use PS3 as an entertainment server via UBUNTU is fading fast....lol

---

### Post by caljohnsmith on 2009-05-02
> **bonzi said:**
> Nope still no luck.

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total[COLOR=Red] 312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   200648519   100324228+   7  HPFS/NTFS
/dev/sda2       200648704   292808703    46080000    7  HPFS/NTFS
/dev/sda3       292816755   296800858     1992052   82  Linux swap / Solaris
/dev/sda4       296800859   [COLOR=Red]312592769[/COLOR]     7895955+   f  W95 Ext'd (LBA)
/dev/sda5       296800875   312576698     7887912   83  Linux
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!     

```

Can I solve the prob by removing the ext3 partition?
I wouldn't get rid of the sda5 partition just yet, because actually what happened is that testdisk determined the ending sector of the sda4 partition using the total number of cylinders of the drive (which is usually a rounded number), rather than using the total sectors of the HDD, so sometimes testdisk erroneously sets the ending sector of the extended partition outside of the drive. There is an option in testdisk where you can force testdisk to write the extended partition so that its  size is based on the logical partitions it contains, rather than making the extended partition's ending sector extend to the end of the drive. But I can't remember at what point when you go through the deep search process you are offered that option; maybe meierfra remembers and can let us know. :)

So how about we try using sfdisk again to correct the ending sector of your sda4 partition, because I think that's the quickest and easiest method; and it will also give us a chance to see if sfdisk modifies any of your other partition boundaries like meierfra pointed out it might be doing due to a bug. So how about again running:
```
echo "296800859,15775840,f" | sudo sfdisk --no-reread -fuS /dev/sda -N4
```
And as usual, reboot, and please post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
And we can work from there.

John

---

### Post by caljohnsmith on 2009-05-02
> **charliko said:**
> Hi    I read this thread with great interest.  I know that my partition tables are corrupt.  I also know that I would like to simply wipe the disks and start over with Ubuntu and Vista.  I have tried to wipe and rewipe.  Still can run Windows if i leave the install disk in the optical drive, but then use Wubi to start Ubuntu.  While I wait for some code solutions to the Belkin USB and 9.4 wifi issues (being connected to my access point but not the internet as well as encryption confusion on my part), I would like to get things right with these two hard drives.

Regarding the hard drives with all the corrupted partition tables, as well as the inability to read iso's on the optical drive at boot up, am i doomed to just buy new hard drives to set things up correctly??  I have a feeling the answer is yes, buy new hard drives.  

Thanks in advance for any input.

-Charlie......my original project to use PS3 as an entertainment server via UBUNTU is fading fast....lol
So do you have any idea how your HDDs ended up with corrupt partition tables? Also, I'm curious, but why do you think you should replace them at this point? Do you have evidence that they are failing hardware-wise? I don't think you mentioned that specifically in your post. Also, have you run any HDD diagnostic tests on them to check their health (such as a SMART test)? Does Windows install OK or did you run into problems? If you would like some help, how about first posting:
```
sudo fdisk -lu
```
And we can work from there if you want.

John

---

### Post by bonzi on 2009-05-02
Hurray!!! Problem solved...
Thank you very much John for helping me these two days. Atlast I have a sigh of relief.

Another reason to love ubuntu is this excellent support from the community.:)

---

### Post by caljohnsmith on 2009-05-02
> **bonzi said:**
> Hurray!!! Problem solved...
Thank you very much John for helping me these two days. Atlast I have a sigh of relief.

Another reason to love ubuntu is this excellent support from the community.:)
That's great news, bonzi. I hope installing and customizing Ubuntu goes smoother for you now. :)

Cheers,
John

---

### Post by bonzi on 2009-05-02
btw I have a doubt what is the meaning of 'f' in and what are the other possible options?
echo "xxxxxxx,yyyyyyy,f"

Okie I got it. Its the System type. Eg if you have HPFS/NTFS use 7 Linux its 83 swap 82 etc.

---

### Post by caljohnsmith on 2009-05-02
> **bonzi said:**
> btw I have a doubt what is the meaning of 'f' in and what are the other possible options?
echo "xxxxxxx,yyyyyyy,f"

Okie I got it. Its the System type. Eg if you have HPFS/NTFS use 7 Linux its 83 swap 82 etc.
Glad you figured it out; BTW, if you want complete listing of all the file systems and their corresponding IDs, you can do:
```
sfdisk -T
```

John

---

### Post by charliko on 2009-05-02
> **caljohnsmith said:**
> So do you have any idea how your HDDs ended up with corrupt partition tables? Also, I'm curious, but why do you think you should replace them at this point? Do you have evidence that they are failing hardware-wise? I don't think you mentioned that specifically in your post. Also, have you run any HDD diagnostic tests on them to check their health (such as a SMART test)? Does Windows install OK or did you run into problems? If you would like some help, how about first posting:
```
sudo fdisk -lu
```And we can work from there if you want.

John

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?   218129509  1920119918   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07dd56b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sdb2       268414020   312576704    22081342+   f  W95 Ext'd (LBA)
/dev/sdb5       268414083   312576704    22081311    7  HPFS/NTFS
char@ubuntu:~$ 
```

hope this helps

-charlie

---

### Post by charliko on 2009-05-03
> **charliko said:**
> ```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?   218129509  1920119918   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07dd56b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sdb2       268414020   312576704    22081342+   f  W95 Ext'd (LBA)
/dev/sdb5       268414083   312576704    22081311    7  HPFS/NTFS
char@ubuntu:~$ 
```hope this helps

-charlie



I am sure this is quite a mess to the skilled person reading it.   I had to go back to DOS at one time to just get something in the system to work.  I thought many times that if I did a low level format that the partition table would disappear; probably the wrong assumption.  The lesson learned is that partition tables need my respect.  Hope you see some chances with this!

-charlie

---

### Post by caljohnsmith on 2009-05-03
Charliko, it looks like the partition table on your 160 GB sdb drive is OK, but the partition table on your 320 GB sda drive definitely seems messed up. Do you want to try and repair the partition table on your sda drive, or do you want to just wipe the drive clean and start over like you said in your original post? Also, do you have any idea how your sda drive's partition table became corrupt? If we knew that, it would help determine whether it might be worth it to try and fix the partition table on that drive. 

Also, please also post the output of the following commands:
```
sudo mkdir /mnt/sdb{1,5}
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdb5 /mnt/sdb5
ls -l /mnt/sdb{1,5}
```

John

---

### Post by charliko on 2009-05-03
> **caljohnsmith said:**
> Charliko, it looks like the partition table on your 160 GB sdb drive is OK, but the partition table on your 320 GB sda drive definitely seems messed up. Do you want to try and repair the partition table on your sda drive, or do you want to just wipe the drive clean and start over like you said in your original post? Also, do you have any idea how your sda drive's partition table became corrupt? If we knew that, it would help determine whether it might be worth it to try and fix the partition table on that drive. 

Also, please also post the output of the following commands:
```
sudo mkdir /mnt/sdb{1,5}
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdb5 /mnt/sdb5
ls -l /mnt/sdb{1,5}
```John


Acutally I would be happy to wipe all the drives clean and start over.  The problem is that it never seems that they truely get wiped.  The optical drives do not even see the iso for ubuntu for example.  I have just assumed that wiping is not the solution, but I do lack the experience.  i may try to manually disconnect the SATA drive and see what happens.  I will have to do the other commands as the 9.4 is saying its connected to internet, but i cannot use the internet with it.  

Thanks again, 

-charlie

---

### Post by caljohnsmith on 2009-05-03
OK, if you want to make the drives appear to be unformatted and "wiped clean", you can run the following commands:
```
sudo dd if=/dev/zero of=/dev/sda count=1
sudo dd if=/dev/zero of=/dev/sdb count=1
```
What those commands do is zero-out the MBR (Master Boot Record) of both drives, and the MBR contains the HDD's partition table. So essentially the drives will appear unformatted after you run the above commands, without having to actually zero-out every sector on the HDD (which is unnecessary). After that you should be able to repartition them and reinstall your OSes, assuming that your CD/DVD drive works OK (sounds like you are having problems with that). Good luck and let me know how it goes.

John

---

### Post by charliko on 2009-05-04
> **caljohnsmith said:**
> OK, if you want to make the drives appear to be unformatted and "wiped clean", you can run the following commands:
```
sudo dd if=/dev/zero of=/dev/sda count=1
sudo dd if=/dev/zero of=/dev/sdb count=1
```What those commands do is zero-out the MBR (Master Boot Record) of both drives, and the MBR contains the HDD's partition table. So essentially the drives will appear unformatted after you run the above commands, without having to actually zero-out every sector on the HDD (which is unnecessary). After that you should be able to repartition them and reinstall your OSes, assuming that your CD/DVD drive works OK (sounds like you are having problems with that). Good luck and let me know how it goes.

John

Hello again John:

Well I should have known better.  After some hours, I am still back where I started;  To boot I have to have an WINDOWS install disc in the DVD/CD opticals.  If I dont do this, I get a message to insert a system disk.  It still doesnt recognize my ubuntu iso or other cds, only windows install discs (while booting).  My theory is that somehow windows has control via another file located elsewhere on the hard drives.  To be more puzzling, when i installed ubuntu again with wubi, I did not have to name the driver for my usb Belkin wireless device.    

I did a few commands that you had sent earlier; I now have VISTA on the smaller (160 gb) drive.  When I started to load VISTA both drives were seen with about  20 gig less memory available.  The option to extend the disk was not available in the VISTA program commands.  I do not know if you would like to continue or not  but here are the results of the commands....since i put VISTA on the other drive and left the 320 gb drive unformatted (except the missing gb's?) I was surprised to get these results.
	 	 har@ubuntu:~$ sudo fdisk -lu  
 [sudo] password for char:  
 

 Disk /dev/sda: 320.0 GB, 320072933376 bytes  
 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x4a769495  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1            2048   625139711   312568832    6  FAT16  
 

 Disk /dev/sdb: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x4a769496  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   *        2048   312578047   156288000    7  HPFS/NTFS  
 char@ubuntu:~$ sudo mkdir /mnt/sdb{1,5} 
 char@ubuntu:~$ sudo mount /dev/sdb1 /mnt/sdb1  
 char@ubuntu:~$ sudo mount /dev/sdb5 mnt/sdb5  
 mount: mount point mnt/sdb5 does not exist  
 char@ubuntu:~$ ls -l /mnt/sdb{1,5}  
 /mnt/sdb1:  
 total 6595753  
 -rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat  
 drwxrwxrwx 1 root root       4096 2009-05-04 00:06 Boot  
 -rwxrwxrwx 1 root root     438840 2006-11-02 04:53 bootmgr  
 -rwxrwxrwx 1 root root       8192 2009-05-04 00:06 BOOTSECT.BAK  
 -rwxrwxrwx 2 root root         10 2006-09-18 17:43 config.sys  
 drwxrwxrwx 1 root root          0 2006-11-02 08:02 Documents and Settings  
 -rwxrwxrwx 1 root root 3219709952 2009-05-04 05:05 hiberfil.sys  
 drwxrwxrwx 1 root root          0 2009-05-04 05:01 NVIDIA  
 -rwxrwxrwx 1 root root 3533635584 2009-05-04 05:05 pagefile.sys  
 drwxrwxrwx 1 root root       4096 2009-05-04 05:05 ProgramData  
 drwxrwxrwx 1 root root       8192 2009-05-04 04:41 Program Files  
 drwxrwxrwx 1 root root          0 2009-05-03 14:19 $Recycle.Bin  
 drwxrwxrwx 1 root root       8192 2009-05-04 05:01 System Volume Information  
 drwxrwxrwx 1 root root          0 2009-05-03 16:59 ubuntu  
 drwxrwxrwx 1 root root       4096 2009-05-03 14:19 Users  
 drwxrwxrwx 1 root root      16384 2009-05-04 05:06 Windows  
 -rwxrwxrwx 1 root root     197915 2009-05-03 17:14 wubildr  
 -rwxrwxrwx 1 root root       8192 2009-05-03 17:14 wubildr.mbr  
 

 /mnt/sdb5:  
 total 0  
 char@ubuntu  
 char@ubuntu:~$ 



I hope I didnt lose anything in the process of getting it here through open office!

Thanks in advance if you see the puzzle a bit better and wish to continue

-charlie

---

### Post by caljohnsmith on 2009-05-04
> **charliko said:**
> To boot I have to have an WINDOWS install disc in the DVD/CD opticals.  If I dont do this, I get a message to insert a system disk.  It still doesnt recognize my ubuntu iso or other cds, only windows install discs (while booting).  My theory is that somehow windows has control via another file located elsewhere on the hard drives.  
To boot the Vista you have on the 160 GB drive, you have to set that drive to be first in your BIOS boot order. And if you can boot your Windows install CD but not the Ubuntu Live CD, you might need to reburn the Ubuntu Live CD at a slower speed or something like that to get it working. When you say the computer "doesn't recognize my ubuntu iso or other cds", what exactly happens when you try to boot the Ubuntu Live CD on start up? Do you get any errors? Also, Windows does not put a file somewhere on one of your HDDs so that it takes sole control of your computer and prevents you from booting other CDs. 
> 
I did a few commands that you had sent earlier; I now have VISTA on the smaller (160 gb) drive.  When I started to load VISTA both drives were seen with about  20 gig less memory available.  
Your drives are reported correctly by fdisk, i.e. the first one is 320 GB and the second one is 160 GB. I think you are getting confused by the fact that a 320 GB HDD is 320,000,000,000 bytes, because the manufacturers are using the decimal definition of Giga as 1,000,000,000 bytes. Yet Vista or any OS uses the binary definition of Giga which is  
1024*1024*1024 = 1,073,741,824 bytes. Thus in Vista or Ubuntu your 320 GB HDD will look like:
```
320,000,000,000 / 1,073,741,824 = 298 GiB
```
So your HDD looks like it is about 20 GB less than the advertised 320 GB value. 

John

---

### Post by charliko on 2009-05-04
[quote=caljohnsmith;7210877]To boot the Vista you have on the 160 GB drive, you have to set that drive to be first in your BIOS boot order. And if you can boot your Windows install CD but not the Ubuntu Live CD, you might need to reburn the Ubuntu Live CD at a slower speed or something like that to get it working. When you say the computer "doesn't recognize my ubuntu iso or other cds", what exactly happens when you try to boot the Ubuntu Live CD on start up? Do you get any errors? Also, Windows does not put a file somewhere on one of your HDDs so that it takes sole control of your computer and prevents you from booting other CDs. 

Your drives are reported correctly by fdisk, i.e. the first one is 320 GB and the second one is 160 GB. I think you are getting confused by the fact that a 320 GB HDD is 320,000,000,000 bytes, because the manufacturers are using the decimal definition of Giga as 1,000,000,000 bytes. Yet Vista or any OS uses the binary definition of Giga which is  
1024*1024*1024 = 1,073,741,824 bytes. Thus in Vista or Ubuntu your 320 GB HDD will look like:
```
320,000,000,000 / 1,073,741,824 = 298 GiB
```So your HDD looks like it is about 20 GB less than the advertised 320 GB value. 

These Bios or CMOS? settings do not give me any option but cd.  The 160 gb hd is set up as the master.  The 320 gb sata is in its own listing.  I am not sure why but I have three different iso's of various versions and none of them get recognized when I try to boot them...I only get the "...insert a system disk and press enter" message.  The only time during a boot up that I am asked to hit a key to run cd or dvd is when I have a Windows install disk in the tray.  It just doesnt recognize the iso's.   

Can other BIOS' be installed with a certain mb??  You are correct....I didnt realize the values of the HD memory could be so far off.  Presently i can run on WUBI, but am waiting for some fix re:  the Belkin is connecting to my wireless, but for some reason has only accessed the internet once.   

At any rate thanks for the help, is it possible it is just my particular hard ware setup then?  However, I have had other dual boot setup's installed just fine in the past.  

Thanks again, 

-charlie

---

### Post by charliko on 2009-05-12
yes  much of the problems i had were due to master slave issues and finally realizing that setup can change cd roms order   etc.  I still have my usb wifi access  problems but have everything isntalled and working now.

Thanks again

---

### Post by BrokenPoet on 2009-06-23
Greetings!  I have a similar issue to those described above.  The only system changes that may have caused the partition tables to change were a) Upgrade (not fresh install) to 9.04 from 8.10 or b) Installation of Vista SP1 (? Whichever was most recent, I don't boot into it frequently.)

Can someone provide guidance as to the correct sfdisk command to repair my tables?  I noted the problem when trying to perform a fresh install of 9.04, as the upgrade version had impacted my wireless and Nvidia drivers.

Thanks!

```
~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   619898880   625139711     2620416    c  W95 FAT32 (LBA)
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   114370551    46610428    7  HPFS/NTFS
/dev/sda4       114382861   625139711   255378425+   f  W95 Ext'd (LBA)
/dev/sda5       619898880   625139711     2620416   dd  Unknown
/dev/sda6       114382863   153436814    19526976   83  Linux
/dev/sda7       153436878   615980294   231271708+  83  Linux
/dev/sda8       615980358   619884089     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=619898880, size=  5240832, Id= c, bootable
/dev/sda2 : start=   178176, size= 20971520, Id= 7
/dev/sda3 : start= 21149696, size= 93220856, Id= 7, bootable
/dev/sda4 : start=114382861, size=510756851, Id= f
/dev/sda5 : start=619898880, size=  5240832, Id=dd
/dev/sda6 : start=114382863, size= 39053952, Id=83
/dev/sda7 : start=153436878, size=462543417, Id=83
/dev/sda8 : start=615980358, size=  3903732, Id=82

~$ sudo parted /dev/sda1 print
Model: Unknown (unknown)
Disk /dev/sda1: 2683MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2683MB  2683MB  fat32  
```

---

