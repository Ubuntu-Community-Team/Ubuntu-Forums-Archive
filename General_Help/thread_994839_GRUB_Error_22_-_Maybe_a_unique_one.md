---
title: "GRUB Error 22 - Maybe a unique one"
date: 2008-11-27
forum: General Help
---

### Post by Jojan on 2008-11-27
So yesterday I was thinking of repartitioning my hard drive a bit to maybe install another distro. So I opened the "Partition Editor" and I believe I did nothing to erase something, but today when I boot up my computer GRUB gave me "Error 22". I've looked around and there are ways to restore GRUB with a live CD, and I tried that with no success.

I have now started the Partition Editor on the live CD and it says that I have circa 700 GiB unallocated. Can this be a part of the problem? How do I fix this? I hope my hard drive isn't erased. I did get a warning when I was using Partition Editor yesterday that if I pressed 'Yes' my hard drive would get erased, so I pressed 'No'.

Please help.

---

### Post by geirha on 2008-11-27
Install [apt://testdisk](apt://testdisk) and have it analyze your harddrive, it may be able to recover your partitions.

It's a command-line tool, so run it in a terminal
```
sudo testdisk
```

---

### Post by Jojan on 2008-11-27
> **geirha said:**
> Install [apt://testdisk](apt://testdisk) and have it analyze your harddrive, it may be able to recover your partitions.

It's a command-line tool, so run it in a terminal
```
sudo testdisk
```

I can't find testdisk in APT. Perhaps because I'm using the 8.04 live CD. But I downloaded it and is currently running it.

---

### Post by EV500B on 2008-11-27
Go to the link below:
:arrow: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
and download it.
You can also(If you have a floppy disk and a floppy drive) to make a dos bootable disk and then extract the testdisk dos version archive in it. You will be able to launch it in dos mode.
This should be the easiest method, I guess!

---

### Post by Jojan on 2008-11-27
I'm running it now, under the live CD and I can see all the files on the drive. So it doesn't seem to be any wrong with it.

But how do I make it so that GRUB can boot from it again?

---

### Post by Jojan on 2008-11-27
When I'm trying to mount the hard drive 'mount' gives me this:
```
> mount -t ext3 /dev/sda /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
And I am root.
```
> dmesg | tail
[ 8979.566988] Buffer I/O error on device fd0, logical block 0
[ 9502.662035] VFS: Can't find ext3 filesystem on dev sda.
[ 9507.464976] VFS: Can't find an ext2 filesystem on dev sda.
[ 9510.157036] VFS: Can't find ext3 filesystem on dev sda.
[ 9550.983813] end_request: I/O error, dev fd0, sector 0
[ 9563.111781] end_request: I/O error, dev fd0, sector 0
[ 9563.111788] Buffer I/O error on device fd0, logical block 0
[ 9575.256401] end_request: I/O error, dev fd0, sector 0
[ 9575.256407] Buffer I/O error on device fd0, logical block 0
[ 9597.867172] VFS: Can't find ext3 filesystem on dev sda.
```

```
> fdisk -lu

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cb7e2

   Device Boot      Start         End      Blocks   Id  System
```
That can't be too good.

---

### Post by Jojan on 2008-11-27
So I'm not able to mount it, and not able to boot from it. But I can see the files in it, and copying them. All the ones I've copied works.

Edit: So... I might have ruined my partitions. But my stuff is still on it. So couldn't I just tell something how my partitions looked like and then just redo them without erasing anything?

---

### Post by caljohnsmith on 2008-11-27
How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and also select each partition and press "p" to see a directory listing; let me know which partitions give you a directory listing. And lastly, please identify what your partitions should be as well as you can remember.

---

### Post by Jojan on 2008-11-27
Ah. I missed the repository thing.

I got help from another site which failed me a bit. I gave them picture 1 (help) and it came out as image 2 (help2).

> **caljohnsmith said:**
> After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

```
Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 89875 254 63 1443857877
 2 P Linux Swap           89876   0  1 91199 254 63   21270060
 2 P Linux Swap           89876   0  1 91199 254 63   21270060
```

As seen the other site put the swap on wrong place.

> **caljohnsmith said:**
> Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and also select each partition and press "p" to see a directory listing; let me know which partitions give you a directory listing.

```
Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 89876 254 63 1443873942
D Linux LVM               25   0  1 91200 254 63 1464742440
D Linux                60417   2  1 62913 254 63   40114179
D Linux                67303   0  1 68546 254 63   19984860
D Linux Swap           89877   1  1 91200 254 63   21269997


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 739 GB / 688 GiB
```

> **caljohnsmith said:**
> And lastly, please identify what your partitions should be as well as you can remember.

I only have one hard drive, only with Ubuntu. As you can see in the images attached.
[INDENT]--------------------------------[/INDENT]
What the other site told me:
> Type
su
fdisk /dev/sda

press p to list partitions, none should be listed

press n for new partition
press p for primary
press 1 for partition 1
press enter for first cylinder
now type in the last cylinder as 89876

now we need to create your swap partition
press n for new partition
press p for primary
press 2 for partition 2
press enter for first cylinder
now type in the last cylinder as 91200

press p to list partitions, there should be to

we need to set partition 1 as bootable, and partition 2 as SWAP

press a
press 1
partition 1 is now bootable

press t
press 2
type 82
partition two is now SWAP

press p again to see the changes.

now press w to save changes, check in gparted, you should be able to access your files and reboot.

---

### Post by caljohnsmith on 2008-11-27
Who told you to recreate your partitions with fdisk? That can be tricky and a bit dangerous if you are unfamiliar with doing something like that; also it is unnecessary since testdisk basically does all that for you.

---

### Post by Jojan on 2008-11-27
> **caljohnsmith said:**
> Who told you to recreate your partitions with fdisk? That can be tricky and a bit dangerous if you are unfamiliar with doing something like that; also it is unnecessary since testdisk basically does all that for you.

It's not someone I know. But that person seemed to be knowing what to do.

But how do I fix this with testdisk, then? Something failed so I had to reboot the LiveCD and restart that deep search, it's up to 90% now.

---

### Post by Jojan on 2008-11-27
It's finished now:
```
Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 89876 254 63 1443873942
D Linux LVM               25   0  1 91200 254 63 1464742440
D Linux                60417   2  1 62913 254 63   40114179
D Linux                67303   0  1 68546 254 63   19984860
D Linux Swap           89877   1  1 91200 254 63   21269997


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 739 GB / 688 GiB
```

---

### Post by caljohnsmith on 2008-11-27
OK, it looks like the first Linux partition it lists is most likely the correct one, because the swap partition comes right after it. How about using the up/down arrow keys to select the first linux partition it lists above, press "P" to list the files, and if that correctly shows your linux root directory, you're in luck. If that is the case, select each of the partitions and mark the partitions as follows (highlighted in red):
```
Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] Linux                    0   1  1 89876 254 63 1443873942
[COLOR="Red"]D[/COLOR] Linux LVM               25   0  1 91200 254 63 1464742440
[COLOR="Red"]D[/COLOR] Linux                60417   2  1 62913 254 63   40114179
[COLOR="Red"]D[/COLOR] Linux                67303   0  1 68546 254 63   19984860
[COLOR="Red"]P[/COLOR] Linux Swap           89877   1  1 91200 254 63   21269997

```
Note that testdisk will only let you mark the swap partition as "P" or "L", depending on whether it was originally a primary/logical partition, so just use whichever it lets you use. Once you are sure all the partitions are marked exactly as shown above, press enter to proceed, and in the next screen you can choose to write the new partition table. After doing that, reboot, and please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Or if you are really lucky, you might be able to boot right back into Ubuntu on your HDD. Let me know how it goes.

---

### Post by Jojan on 2008-11-27
I was lucky. All that it said was that I had done a false shutdown (or something like that) and it did a little check.

Everythings is as should be, so far. :-)

Thank you for the help.

---

### Post by caljohnsmith on 2008-11-27
Glad that worked; hope that whatever happened to you with using gparted on your HDD doesn't happen again. Cheers and have fun with Ubuntu. :)

---

### Post by Jojan on 2008-11-27
> **caljohnsmith said:**
> Glad that worked; hope that whatever happened to you with using gparted on your HDD doesn't happen again. Cheers and have fun with Ubuntu. :)

Yeah. But at least I now know how to solve it!

I've been using Ubuntu for almost a year as my operating system. I have had Ubuntu for over a year on my laptop, which I mostly use in school.

---

