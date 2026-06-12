---
title: "Bad partition table"
date: 2008-11-08
forum: Hardware
---

### Post by CanasClone on 2008-11-08
I can't install the new ubuntu because it does not recognize my computer's partition table (shows it as one partition in gparted). I used a tool called testdisk to view partition properties and got this:

[IMG]http://i12.photobucket.com/albums/a211/CanasClone/Partitions.jpg[/IMG]

Anyone know how to fix the sectors of that without deleting my windows data? I am willing to format the other partitions. This is also dangerous because windows does not recognize the OSs on the machine (just it now) and so it boots to a dead grub (spits out an error cause it's not there). I have to use a USB boot manager to get to my computer which is dangerous to have my computer depend on it to run. Thanks!

---

### Post by CanasClone on 2008-11-08
No one?

---

### Post by SaltySurfer on 2008-11-08
which version of windows are you running?

---

### Post by caljohnsmith on 2008-11-08
I can help you use testdisk if you like, because I have experience helping others recover their partition tables with it. Please first post:
```
sudo fdisk -l
```
Then run testdisk again:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition table, and also let me know to the best of your knowledge what your partitions should be. We can work from there. :)

---

### Post by CanasClone on 2008-11-08
Thanks for for caring guys! I am running Windows Vista. I booted 8.10 Live CD and got the following:

Results of fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29e3de20

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14422       14593     1381590   82  Linux swap / Solaris
/dev/sda2   ?           1       10769    86501961    7  HPFS/NTFS
/dev/sda3           13147       14421    10241437+   c  W95 FAT32 (LBA)
/dev/sda4           10770       13146    19093252+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
```

testdisk initial scan:
```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Linux Swap           14421   0  1 14592 254 63    2763180
 2 * HPFS - NTFS              0   1  1 10768 254 63  173003922 [Windows Partitio
 3 P FAT32 LBA            13146   0  1 14420 254 63   20482875 [NO NAME]
 4 P Linux                10769   0  1 13145 254 63   38186505










*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

The results of the deeper search:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 10768 254 63  173003922 [Windows Partition]
D HPFS - NTFS              0   1 10 10768 254 63  173003913
* Linux                10769   0  1 13145 254 63   38186505
P FAT32 LBA            13146   0  1 14420 254 63   20482875 [NO NAME]
P Linux Swap           14421   0  1 14592 254 63    2763180








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 88 GB / 82 GiB
```

Ideally my partitions are:
~80 gig NTFS (Vista)
~10 gig Ext3 (/)(I formatted it to FAT32 arbitrarily in case that was the problem partition, but it didn't work)
~1.4 gig Swap
~17 gig Ext3 (/home)

---

### Post by caljohnsmith on 2008-11-08
Your partition table structure looks fine, and testdisk did not report any errors either. I'm not sure why gparted would show the drive as only one partition; how about running gparted by doing:
```
gksudo gparted
```
And then post a screen shot of gparted showing the single partition. Also, check the terminal where you ran the above gparted command to see if it reports any errors/warnings.

Also, one small question, but in the fdisk output you posted, did it really have a question mark (?) next to sda2? That should be an asterisk (*).

---

### Post by CanasClone on 2008-11-08
Well if you look at the testdisk output of the deep scan the partition appears twice and shows two different sizes. The weirdest part is that beside them it shows a "D" which stands for deleted, but it's obviously not deleted cause I can boot from it. Yes, that question mark is really there.

When I run gksudo gparted, here's the terminal output:

```
ubuntu@ubuntu:~/Desktop/testdisk-6.10/linux$ gksudo gparted
======================
libparted : 1.8.9
======================
/dev/sda: unrecognised disk label
```

as for the screenshot:

[IMG]http://i12.photobucket.com/albums/a211/CanasClone/Gpartedscreencap.png[/IMG]

---

### Post by Steve1961 on 2008-11-08
I had a similar error when trying to install Ubuntu on my eeepc.  That was because of an efi disc label that gparted doesn't support.  In the end I just used dd to wipe the partition table and started fresh.  That worked fine, but it's perhaps a bit drastic for you.

---

### Post by caljohnsmith on 2008-11-08
Don't worry that testdisk showed your Windows partition as "D" after the deep scan, because when it does a deep scan, it just gives you a suggested partition table with all partitions found, which is often nothing like what your current partition table shows. 

The fact that you are still having problems with gparted, and that fdisk has a question mark next to sda2 make me think that it would definitely be worth having testdisk rewrite your partition table. From your deep scan output:
```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1 10768 254 63  173003922 [Windows Partition]
[COLOR="Red"]D[/COLOR] HPFS - NTFS              0   1 10 10768 254 63  173003913
[COLOR="Red"]P[/COLOR] Linux                10769   0  1 13145 254 63   38186505
[COLOR="Red"]P[/COLOR] FAT32 LBA            13146   0  1 14420 254 63   20482875 [NO NAME]
[COLOR="Red"]P[/COLOR] Linux Swap           14421   0  1 14592 254 63    2763180
```
How about marking the partitions as I've shown above, press "enter" to get the next screen, and then choose to write the new partition table. Then reboot, and see if gparted is able to recognize the partitions. Let me know how it goes.

---

### Post by CanasClone on 2008-11-08
I found a little tutorial on it from the guys who made testdisk and they showed a problem almost the same as mine. I tried to look at the file lists of the partitions and only the top one of the repeated partition showed anything, so I tried to do what you said and when I hit write it said that it had done it (although strangely fast) and would require a reboot. I rebooted and it shows the same thing again. I'm gonna try it again and will tell you about it, but do you think there is any reason why it wouldn't work off a live CD?

---

### Post by caljohnsmith on 2008-11-08
Testdisk will run just fine from the Live CD, so I'm almost sure that's not the problem. Also, the partition table is only 64 bytes in the MBR (Master Boot Record), so it shouldn't take any time to write it. Does your fdisk output still show sda2 with a question mark under the boot heading? How about posting fdisk again:
```
sudo fdisk -l
```

---

### Post by CanasClone on 2008-11-09
It works! It recognizes my partition table and I installed Ubuntu 8.10! Thank you so much!

Whenever I allowed the harddrive to boot it would revert the table to the broken partition format. All I had to do was fix it with testdisk as you told me then boot again straight into the live CD to install. Now it's all fixed! Thank you!

---

### Post by caljohnsmith on 2008-11-09
That's great news you eventually got it to work. Hopefully you won't have any more problems with your partition table any time soon. Cheers and have fun with Ubuntu. :)

---

