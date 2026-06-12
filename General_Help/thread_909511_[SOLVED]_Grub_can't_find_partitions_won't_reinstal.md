---
title: "[SOLVED] Grub can't find partitions/ won't reinstall after windows"
date: 2008-09-03
forum: General Help
---

### Post by Vock on 2008-09-03
My windows xp dual boot recently crashed, and i had to reinstall windows on it's own separate partition. Doing so naturally messed up my MBR and grub no longer boots and goes directly to windows. 

What I've Tried so far:

```
sudo grub
find /boot/grub/stage1
```


This outputs:

```
(hd0,7)
```


Then I do:

```
root (hd0,7)
setup (hd0)
```


from that I get the following: 


```
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,7)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
```


Looked around on the forums and found another method, tried that:

From sudo fdisk -l

```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5f3e5f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda3           19014       19456     3558397+  82  Linux swap / Solaris
/dev/sda5            3825       15632    94847697    b  W95 FAT32
/dev/sda6           15633       17685    16490691   83  Linux
/dev/sda7           17686       19013    10667128+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1f277d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
```


Since, from the Live CD i am able to mount/browse my individiual partitions, i know that my 11 GB partition is the one with the /boot/grub directory on it

```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1014M   16M  998M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                1014M   16M  998M   2% /lib/modules/2.6.24-16-generic/volatile
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   68K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
tmpfs                1014M   16K 1014M   1% /tmp
gvfs-fuse-daemon     1014M   19M  996M   2% /home/ubuntu/.gvfs
/dev/sda6              16G  1.7G   14G  11% /media/disk
/dev/sda7              11G  4.7G  5.0G  49% /media/disk-1
/dev/sda1              30G   22G  8.3G  72% /media/disk-2
/dev/sda5              91G   89G  2.3G  98% /media/disk-3
/dev/sdb1             466G  295G  172G  64% /media/Local Disk
```


from here I tried the following: 

```
mkdir /mnt/root
sudo mount -t ext3 /dev/sda7 /mnt/root
sudo grub-install --root-directory=/mnt/root /dev/sda7
```


This gave me this error:
```

The file /mnt/root/boot/grub/stage1 not read correctly.

```

From there, trying the following:
```

sudo mount -o bind /dev /mnt/root/dev
sudo mount -o bind /proc /mnt/root/proc
sudo cp /proc/mounts /mnt/root/etc/mtab
sudo chroot /mnt/root/ /bin/bash
sudo mount /dev/sda7 /boot
sudo /sbin/grub-install /dev/sda7

```

Output:
```

You shouldn't call /sbin/grub-install. Please call /usr/sbin/grub-install instead!

Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

```

I'm guessing my grub is corrupted? anyway i can avoid wiping everything and reinstalling from scratch?

And if I need to reinstall, is there anyway I can do it and keep my /home partition? Currently the LiveCD installer doesn't recognize any of the partitions on my first hard drive sda...

---

### Post by caljohnsmith on 2008-09-03
> **Vock said:**
> 
```
sudo grub
find /boot/grub/stage1
```


This outputs:

```
[COLOR="Red"](hd0,7)[/COLOR]
```

From sudo fdisk -l

```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5f3e5f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda3           19014       19456     3558397+  82  Linux swap / Solaris
/dev/sda5            3825       15632    94847697    b  W95 FAT32
/dev/sda6           15633       17685    16490691   83  Linux
[COLOR="Red"]/dev/sda7 [/COLOR]          17686       19013    10667128+  83  Linux

Something must be wrong, because (hd0,7) is actually sda8, not sda7, and you don't even have an sda8 partition according to fdisk. I think it would be prudent to check your partition table with testdisk and see if maybe it is corrupted. From the Live CD try:
[CODE]sudo apt-get install testdisk
sudo testdisk
```
Go through the prompts in testdisk until you get to the point where you select "analyze", and then see if testdisk returns any errors when it prints out your partition table. Also, please post the output. Let me know how it goes or if you need any more details/info.

---

### Post by cdtech on 2008-09-03
Here is the official Ubuntu method:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Vock on 2008-09-03
Here is a screen shot of the output, as far as I can tell there are no errors. I think maybe that it says sda7 because it skips over sda4? Not entirely sure of that...

[IMG]http://img66.imageshack.us/img66/2532/screenshotubuntuubuntumd0.png[/IMG]

Never installed Vista, so told it to skip searching for Vista Partitions, now sitting at this screen:

[IMG]http://img222.imageshack.us/img222/4807/screenshotubuntuubuntu1hv5.png[/IMG]

@CDTech

Everything from after the sudo fdisk -l was from the official Ubuntu method, still stuck...

---

### Post by Vock on 2008-09-03
.

---

### Post by caljohnsmith on 2008-09-03
Unfortunately, like I suspected, your partition table is messed up right now; in that first screenshot, testdisk says "Space conflict between the following two partitions", meaning extended partition (sda2) and the primary swap partition (sda3). In other words, sda3 should be a logical partition since it is inside sda2, but somehow the partition table thinks its a primary partition. Just use testdisk to change sda3 from a primary partition to a logical partition that's inside of sda2. And then go through the analyze stage again to make sure it doesn't return any more errors like that. Let me know how it goes.

---

### Post by Vock on 2008-09-03
I am actually having some difficulty figuring out how to use Testdisk to fix this. I tried looking around, and all I've found is people say it's so easy and haven't actually written down what they did to fix the problem.

From the second screen shot, i just hit enter to continue,
```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3823 254 63   61432497
 2 E extended LBA          3824   0  1 19455 254 63  251128080
 5 L HPFS - NTFS           3824   1  1 19455 254 63  251128017












[  Quit  ]  [Search! ]  [ Write  ]  [Extd Part]
                   Search deeper, try to find more partitions

```

I tell it to search, as my partitions are missing and i get the following:
```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3823 254 63   61432497
D HPFS - NTFS           3824   1  1 19455 254 63  251128017
D FAT32 LBA             3824   2  1 15631 254 63  189695394
D Linux                15632   1  1 17684 254 63   32981382
D Linux                17685   1  1 19012 254 63   21334257
D Linux Swap           19013   0  1 19455 254 63    7116795







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 31 GB / 29 GiB

```

Is it suggesting i delete all my partitions? Not entirely sure where to go from here.

Thanks for all your help thus far.

Edit: 
in the above, the only available types I can change to are Primary Bootable, Primary and Deleted, can't switch to Logical or Extended for those partitions.

---

### Post by caljohnsmith on 2008-09-03
First of all, from your fdisk output in your original post, are the partitions there correct? If you think they are, then just use testdisk to relabel the partitions as follows:
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3823 254 63   61432497
[COLOR="Red"]E[/COLOR] HPFS - NTFS           3824   1  1 19455 254 63  251128017
[COLOR="Red"]L[/COLOR] FAT32 LBA             3824   2  1 15631 254 63  189695394
[COLOR="Red"]L[/COLOR] Linux                15632   1  1 17684 254 63   32981382
[COLOR="Red"]L[/COLOR] Linux                17685   1  1 19012 254 63   21334257
[COLOR="Red"]L[/COLOR] Linux Swap           19013   0  1 19455 254 63    7116795

```
Select the partition to modify, then use right/left arrow keys to change the partition type. Let me know how it goes.

EDIT: if you can't change the partition entries in the screenshot you posted to logical, I think you have to keep going by pressing "enter" and getting to the screen where it has the "search!" option--that will do a deep search, and when it is finished you can modify the necessary partitions to be logical.

---

### Post by Vock on 2008-09-04
I'm at the screen where I can change them after the search! option, but I can't select Extended for the second HPFS - NTFS, and can only selected Deleted, Primary Bootable or Primary for the Linux Swap partition

---

### Post by caljohnsmith on 2008-09-04
> **Vock said:**
> I'm at the screen where I can change them after the search! option, but I can't select Extended for the second HPFS - NTFS, and can only selected Deleted, Primary Bootable or Primary for the Linux Swap partition
I tried testdisk on my own HDD, and I had the exact same experience as you: it wouldn't let me label a partition as extended. But I noticed that if I mark the extended partition as deleted, but correctly mark the partitions in it as logical, when I "proceed" and go to the next screen, testdisk creates the correct extended partition to contain the logical partitions. Give that a try, you have nothing to lose if you try that, because testdisk hasn't yet touched your HDD's partition table; you can always go back and try something else.

---

### Post by Vock on 2008-09-04
Leave the linux swap partition as deleted as well then? I can't change it to logical for some reason, only Primary or Primary Bootable

Edit: Linux swap partition is already primary  ( in the first screen shot, just noticed), I'm going to give that a try. Sorry about the many posts, just scared to do something without consulting you, as I don't really know what I'm doing and don't want to muck everything up. Thanks for all the help again thus far.

---

### Post by caljohnsmith on 2008-09-04
Can you post a screen shot of the partitions in testdisk you are seeing right now? That would help me figure out what the problem could be.

---

### Post by Vock on 2008-09-04
From the first analyse screen theres:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3823 254 63   61432497
 2 E extended LBA          3824   0  1 19455 254 63  251128080
 3 P Linux Swap           19013   0  1 19455 254 63    7116795
Space conflict between the following two partitions
 2 E extended LBA          3824   0  1 19455 254 63  251128080
 3 P Linux Swap           19013   0  1 19455 254 63    7116795
   X extended              3824   0  2 15631 254 63  189695519
 5 L FAT32                 3824   2  1 15631 254 63  189695394
   X extended             15632   0  1 17684 254 63   32981445
 6 L Linux                15632   1  1 17684 254 63   32981382
   X extended             17685   0  1 19012 254 63   21334320
 7 L Linux                17685   1  1 19012 254 63   21334257


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

```

It shows the Linux Swap Partition as a Primary Partition.

After doing the search! I get this screen:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3823 254 63   61432497
D HPFS - NTFS           3824   1  1 19455 254 63  251128017
D FAT32 LBA             3824   2  1 15631 254 63  189695394
D Linux                15632   1  1 17684 254 63   32981382
D Linux                17685   1  1 19012 254 63   21334257
D Linux Swap           19013   0  1 19455 254 63    7116795







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 31 GB / 29 GiB

```

and I'm thinking of changing it to:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3823 254 63   61432497
D HPFS - NTFS           3824   1  1 19455 254 63  251128017
[COLOR="Red"]L[/COLOR] FAT32 LBA             3824   2  1 15631 254 63  189695394
[COLOR="Red"]L[/COLOR] Linux                15632   1  1 17684 254 63   32981382
[COLOR="Red"]L[/COLOR] Linux                17685   1  1 19012 254 63   21334257
[COLOR="Red"]P[/COLOR] Linux Swap           19013   0  1 19455 254 63    7116795







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 31 GB / 29 GiB

```

since it won't let me change the Linux Swap to L

---

### Post by caljohnsmith on 2008-09-04
I guess if for whatever reason testdisk won't let you make swap a logical partition, go ahead and let it be a primary partition; it shouldn't hurt, since you only have 1 other primary partition and your extended partition.

---

### Post by Vock on 2008-09-04
Made the changes and saved it, afterwords reinstalled grub with root on (hd0,6) like everyone expected.

After that got Grub Error 15: File not found.

Went and looked at my menu.lst, changed the root pointers to (hd0,6), rebooted and worked like a charm.

Thanks a ton for your quick replies and unending help, really appreciated.

---

### Post by caljohnsmith on 2008-09-04
> **Vock said:**
> Made the changes and saved it, afterwords reinstalled grub with root on (hd0,6) like everyone expected.

After that got Grub Error 15: File not found.

Went and looked at my menu.lst, changed the root pointers to (hd0,6), rebooted and worked like a charm.

Thanks a ton for your quick replies and unending help, really appreciated.
You're welcome, and I'm glad that your computer is healthy again. :) Although I'm still wondering why testdisk wouldn't let you make that swap partition part of your extended partition, as that was what it was originally (at least according to fdisk). But at least things are working again for you, and that's ultimately what matters.

---

