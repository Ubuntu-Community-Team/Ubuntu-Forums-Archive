---
title: "Help with partition and GRUB-error 17"
date: 2008-11-14
forum: General Help
---

### Post by DemonKyoto on 2008-11-14
Disclaimer: Linux noob :P

My system is a dual boot, XP and Ubuntu 8.04.

On XP, I decided to use Partition Magic to shrink my XP NTFS partition and add on the removed space to my Ubuntu partition. While Partition Magic was doing its business, I got an error which forced my PC to reboot, and now, GRUB is stuck at:

"GRUB Loading stage 1.5.

GRUG loading, please wait...
Error 17"

so as of right now, I cant boot into either Heron or XP, though I do have the Live CD.

fdisk shows the below
> 
omitting empty partition (5)

Disk /dev/sda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32
/dev/sda2   *         620       15852   115161480    7  HPFS/NTFS
/dev/sda3           15853       21175    40241880    f  W95 Ext'd (LBA)
/dev/sda5           19788       20909     8482257   83  Linux

Any other info needed, just ask. Thanks a lot.

---

### Post by TeXtonyx on 2008-11-14
This can be a big problem. But, start with downloading Super Grub
disk. See if you an boot your Ubuntu partition. Do you have the 
XP install cd? See if you can reinstall grub.

---

### Post by caljohnsmith on 2008-11-14
Do you have your Live CD that you installed Ubuntu with? If so, how about booting that, use the "try Ubuntu without making changes" option at the first menu, and when you get to the desktop, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo fsck -y /dev/sda5
```
And please post the output. If the fsck completes successfully, also post the output of:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt
```
And see if that shows your Ubuntu root directory. If that works, finish with:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And post the output. After that reboot, and you should be OK again. If you don't make it that far, let me know and we can work from there if you want. :)

---

### Post by TeXtonyx on 2008-11-14
Partition Magic: First you choose to resize the Windows partition.
Then it asks you where you want to redistribute your free space,
and I assume OP chose Linux ext 3. So PM starts by moving files
away from the part of the partition which is going to be eliminated
and towards the center or opposite end of the partition.

When it finishes, it writes all the new locations of files so that
Windows knows where they are. Then it moves the boundary of the
partition. If PM gets interrupted before it's finished moving files
and informing Windows of there new location, it is a real mess.
It has happened to me twice and I had to reinstall Windows.

But I tend to think the PM process had gotten past the dangerous
stage because normally messing with the internal structure of the
Windows partition doesn't impact how Linux works. So I think the
last step of PM is to expand the ext3 partition, and that may be
where the process got interrupted. But I don't think PM has to
move any files in order to expand the ext3 partition. Hopefully
it will just be a case of Ubuntu not knowing its own boundaries
for where it can write files to. I seem to recollect that has to
do with inodes and blocks. It may work out that after Ubuntu is 
repaired that the Windows part of the process was completed and 
that XP will boot from the grub menu.

---

### Post by DemonKyoto on 2008-11-14
> **caljohnsmith said:**
> Do you have your Live CD that you installed Ubuntu with? If so, how about booting that, use the "try Ubuntu without making changes" option at the first menu, and when you get to the desktop, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo fsck -y /dev/sda5
```

So for that, I got
> ubuntu@ubuntu:~$ sudo fsck -y /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


> **caljohnsmith said:**
> And please post the output. If the fsck completes successfully, also post the output of:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt
```

Got:

> ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ ls -l /mnt
total 0
ubuntu@ubuntu:~$ 


> **caljohnsmith said:**
> And see if that shows your Ubuntu root directory. If that works, finish with:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```

For reference, when attempting the rest:

[QUOTE]grub> root (hd0,4) 

grub> setup (hd0) 

Error 17: Cannot mount selected partition


---

### Post by caljohnsmith on 2008-11-14
I just noticed from your original post:
> ```
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf806f806

Device Boot Start End Blocks Id System
/dev/sda1 1 619 4679608+ b W95 FAT32
/dev/sda2 * 620 15852 115161480 7 HPFS/NTFS
/dev/sda3 15853 21175 40241880 f W95 Ext'd (LBA)
/dev/sda5 19788 20909 8482257 83 Linux 
```
That "omitting empty partition (5)" warning is usually a definite sign that your partition table is corrupt. You might be able to salvage your sda5 partition with the help of testdisk, so first make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you have Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partition.
[B]
If you have Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partition.

---

### Post by psusi on 2008-11-14
Never use partition magic.  It destroys hard drives, like it has done for you.  Next time use gparted on the livecd.

---

### Post by DemonKyoto on 2008-11-14
> TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 163 GB / 152 GiB - CHS 19929 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (FAT) != 255 (HD)
 1 P FAT32                    0   1  1   582 149 63    9359217 [HP_RECOVERY]

Bad sector count.
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 2 * HPFS - NTFS            582 150  1 14919 134 63  230322960

Bad relative sector.
 3 E extended LBA         14919 135  1 19929 104 63   80483760
   X extended             18623  15  2 19679  14 63   16964639
No EXT2, JFS, Reiser, cramfs or XFS marker
 5 L Linux                18623  16  2 19679  14  1   16964514
 5 L Linux                18623  16  2 19679  14  1   16964514

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition


and the 2nd part:

> TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 163 GB / 152 GiB - CHS 19929 255 63

The harddisk (163 GB / 152 GiB) seems too small! (< 163 GB / 152 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
D Linux Swap           19680   0  1 19929 104 47    4006784










[ Continue ]

SWAP2 version 1, 2051 MB / 1956 MiB


---

### Post by caljohnsmith on 2008-11-14
Is that second sreen you posted the output right after typing "Y/N" when it asks you if you have any Vista partitions? If that is the case, you need to proceed and do the "Search!" or "Deeper Search" so it does a deep scan of your HDD, which should take a while.

---

### Post by DemonKyoto on 2008-11-14
the 2nd part, pasted again below, was the result of the Search! option.

> TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 163 GB / 152 GiB - CHS 19929 255 63

The harddisk (163 GB / 152 GiB) seems too small! (< 163 GB / 152 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
D Linux Swap           19680   0  1 19929 104 47    4006784



[ Continue ]

SWAP2 version 1, 2051 MB / 1956 MiB


---

### Post by caljohnsmith on 2008-11-14
Did it take at least 10 or more minutes to do that deep search? If so, then unfortunately it doesn't look like Testdisk can help you recover your corrupt partition table. If you have important files in Ubuntu that you want to try and recover, you could try following [this post]("http://ubuntuforums.org/showpost.php?p=5806996") to see if using a different file system superblock will allow you to mount the Ubuntu partition and access your files. If that doesn't work, you will probably have to resort to something like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover your individual files off the drive. Good luck and let me know how it goes.

EDIT: By the way, are you sure you ran testdisk with "sudo testdisk"?

---

### Post by DemonKyoto on 2008-11-14
It took about 30 mins, when I came back, that was the screen, and yes I did use sudo. I'll give it another try to be sure.

If all else fails, is there an easy way to get my pc booted into my XP partition? Everything I had was on it, not the ubuntu partition, so I can back that up and just format everything.

---

### Post by caljohnsmith on 2008-11-14
If you want to try and boot into Windows, you can restore the Windows MBR (Master Boot Record) to your drive by booting your Windows Install CD, going to the recovery console, and running:
```
fixmbr
```
If you don't have a Windows install CD, you can instead do the following from Ubuntu:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
Let me know how it goes.

---

### Post by DemonKyoto on 2008-11-14
XP disc wouldnt help, but i got the MBR restored from Live CD, least I wont be losing anything once I format. Now I just have to get all my partitions back down to the single one and format the sucker, thanks.

---

### Post by meierfra. on 2008-11-14
> Disk /dev/sda - 163 GB / 152 GiB - CHS 19929 255 63

The harddisk (163 GB / 152 GiB) seems too small! (< 163 GB / 152 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
Partition Start End Size in sectors
D Linux Swap 19680 0 1 19929 104 47 4006784

[ Continue ]

This is not the main output of the "deep search".  Select "continue" and post the content of the next screen.

---

### Post by directcharitycontribution on 2008-11-14
[http://ubuntuforums.org/tags.php?tag=error+17](http://ubuntuforums.org/tags.php?tag=error+17)

---

### Post by TeXtonyx on 2008-11-14
Any of those partition programs will screw up your data if they are
interrupted in midstream. It's better to use a Linux tool for Linux.

Besides running fixmbr from the XP Recovery Console, run fixboot.

If that doesn't work and you haven't backed up the XP data, then
do a non-destructive reinstall (Repair). It will create a directory
C:\>Windows.000 rather than the present C:\>. It leaves nearly all
the data files in place with the notable exception of My Documents,
maybe a couple of others. The rest of the data will still be there
to easily backup. The big downside is that most of your installed
applications won't work, they will have to be reinstalled. This way 
is much better than formatting if you don't have any important files 
on the XP partition backed up. You need an XP install cd, not an OEM.

---

