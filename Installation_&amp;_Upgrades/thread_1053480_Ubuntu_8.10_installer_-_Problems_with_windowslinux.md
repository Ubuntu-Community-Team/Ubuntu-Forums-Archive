---
title: "Ubuntu 8.10 installer - Problems with windows/linux partition recognition"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by nimnull22 on 2009-01-28
Hi.

I have: 
sudo fdisk -l (from Live CD)

/dev/sda1 *    1    54    204088+  7 HPFS/NTFS
/dev/sda2     55 31010 117013680   5 Extended
/dev/sda3  10336 14398  15358140   7 HPFS/NTFS
/dev/sda5     55  5473  20483788+  7 HPFS/NTFS
/dev/sda6   5474 10335  18378328+  7 HPFS/NTFS
/dev/sda7  14399 14452    204088+ 83 Linux
/dev/sda8  14453 19869  20476228+ 83 Linux
/dev/sda9  19870 20356   1840828+ 83 Linux Swap
/dev/sda10 20357 31010  40272088+ 83 Linux

I have Linux already installed and I have GRAB.

I want to install Ubuntu to the existing Linux partitions, But Ubuntu's installer does not see them. And it does not see any partition on my disk. 
What to do?

Thank you.

---

### Post by taurus on 2009-01-28
> **nimnull22 said:**
> Hi.

I have: 
sudo fdisk -l (from Live CD)

/dev/sda1 *    1    54    204088+  7 HPFS/NTFS
/dev/sda2     55 31010 117013680   5 Extended
/dev/sda3  10336 14398  15358140   7 HPFS/NTFS
/dev/sda5     55  5473  20483788+  7 HPFS/NTFS
/dev/sda6   5474 10335  18378328+  7 HPFS/NTFS
**/dev/sda7  14399 14452    204088+ 83 Linux**
**/dev/sda8  14453 19869  20476228+ 83 Linux**
/dev/sda9  19870 20356   1840828+ 83 Linux Swap
**/dev/sda10 20357 31010  40272088+ 83 Linux**

I have Linux already installed and I have **[COLOR="Red"]GRAB[/COLOR]**.

I want to install Ubuntu to the existing Linux partitions, But Ubuntu's installer does not see them. And it does not see any partition on my disk. 
What to do?

Thank you.

You have three Linux partitions.  What do you plan to mount them?  You need one for / and I assume you would use another one for /home.  What would you do with the third one?

At the partition screen, did you pick the Manual option and try to mount whichever partition you want to / and format that partition.  Then, mount another one to whatever mount point you want and do the same for the third Linux (ext3) partition.

---

### Post by nimnull22 on 2009-01-28
Ubuntu installer does NOT show anything on my HDD in Manual section. Nothing. For it I have empty disk.

---

### Post by taurus on 2009-01-28
What's the output of this command from a terminal (from LiveCD)?

```
df -h
```

---

### Post by caljohnsmith on 2009-01-28
> **nimnull22 said:**
> 
```
sudo fdisk -l (from Live CD)

/dev/sda1 *    1    54    204088+  7 HPFS/NTFS
[COLOR="Red"]/dev/sda2     55 31010[/COLOR] 117013680   5 Extended
[COLOR="Red"]/dev/sda3  10336 14398[/COLOR]  15358140   7 HPFS/NTFS
/dev/sda5     55  5473  20483788+  7 HPFS/NTFS
/dev/sda6   5474 10335  18378328+  7 HPFS/NTFS
/dev/sda7  14399 14452    204088+ 83 Linux
/dev/sda8  14453 19869  20476228+ 83 Linux
/dev/sda9  19870 20356   1840828+ 83 Linux Swap
/dev/sda10 20357 31010  40272088+ 83 Linux
```

It looks like the problem is that your partition table is corrupt; primary partition sda3 is inside the bounds of your extended partition sda2, so sda3 should be a logical partition instead. If you would like some help fixing your partition table, please post the following:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by nimnull22 on 2009-01-28
df -h

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 755M  2.0M  753M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 755M  2.0M  753M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 755M     0  755M   0% /lib/init/rw
varrun                755M  108K  755M   1% /var/run
varlock               755M     0  755M   0% /var/lock
udev                  755M  2.8M  752M   1% /dev
tmpfs                 755M  104K  755M   1% /dev/shm
rootfs                755M  133M  622M  18% /
/dev/scd0             4.3G  4.3G     0 100% /cdrom
/dev/loop0            1.5G  1.5G     0 100% /rofs
tmpfs                 755M   28K  755M   1% /tmp


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
120 heads, 63 sectors/track, 31010 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1ea208d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      408239      204088+   7  HPFS/NTFS
/dev/sda2          408240   234435599   117013680    5  Extended
/dev/sda3        78132600   108848879    15358140    7  HPFS/NTFS
/dev/sda5          408303    41375879    20483788+   7  HPFS/NTFS
/dev/sda6        41375943    78132599    18378328+   7  HPFS/NTFS
/dev/sda7       108848943   109257119      204088+  83  Linux
/dev/sda8       109257183   150209639    20476228+  83  Linux
/dev/sda9       150209703   153891359     1840828+  82  Linux swap / Solaris
/dev/sda10      153891423   234435599    40272088+  83  Linux


ubuntu@ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   408177, Id= 7, bootable
/dev/sda2 : start=   408240, size=234027360, Id= 5
/dev/sda3 : start= 78132600, size= 30716280, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=   408303, size= 40967577, Id= 7
/dev/sda6 : start= 41375943, size= 36756657, Id= 7
/dev/sda7 : start=108848943, size=   408177, Id=83
/dev/sda8 : start=109257183, size= 40952457, Id=83
/dev/sda9 : start=150209703, size=  3681657, Id=82
/dev/sda10: start=153891423, size= 80544177, Id=83

---

### Post by caljohnsmith on 2009-01-28
> **nimnull22 said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
120 heads, 63 sectors/track, 31010 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1ea208d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      408239      204088+   7  HPFS/NTFS
/dev/sda2          408240   234435599   117013680    5  Extended
/dev/sda3        [COLOR="Red"]78132600[/COLOR]   108848879    15358140    7  HPFS/NTFS
/dev/sda5          408303    41375879    20483788+   7  HPFS/NTFS
/dev/sda6        41375943    [COLOR="Red"]78132599[/COLOR]    18378328+   7  HPFS/NTFS
/dev/sda7       108848943   109257119      204088+  83  Linux
/dev/sda8       109257183   150209639    20476228+  83  Linux
/dev/sda9       150209703   153891359     1840828+  82  Linux swap / Solaris
/dev/sda10      153891423   234435599    40272088+  83  Linux

```
In order to fix your partition table, we will need to make sda3 a logical partition, but as you can see highlighted in red above, the sda3 partition starts at the sector right after the sda6 partition. We will first need to shrink your sda6 partition by 63 sectors in order to allow room for the EBR (Extended Boot Record) that needs to go before the sda3 partition in order to make it a logical partition. Although doing a resize of only 63 sectors is really low risk, it would still be a good idea to have your important data on sda6 backed up. Once you've done that, how about doing the following:
```
sudo umount /dev/sda6
sudo ntfsresize --size 18819376128 /dev/sda6
```
The first umount command is to make sure sda6 is not mounted, so it is OK if it says that sda6 is not mounted. Once the resize is done (it should go really fast), please post the output of the above commands, and we can go from there.

---

### Post by BigCityCat on 2009-01-28
I had this issue and someone suggested to use the ubuntu alternate install dvd. It has a more powerful partition manager, and it worked for me. Unfortunately you will have to download the alternate install dvd.

---

### Post by nimnull22 on 2009-01-28
To: Caljohnsmith

Thank you for your help.

But, sda6 and sda3 - windows partitions, and they have information inside.

And anyway, I want to install linux, not to reinstall windows.
What is the problem for linux to install itself to the already prepared partitions sda7, sda8, sda9, sda10.

Can you explain me this first, please.

Thank you.

---

### Post by caljohnsmith on 2009-01-28
> **nimnull22 said:**
> To: Caljohnsmith

Thank you for your help.

But, sda6 and sda3 - windows partitions, and they have information inside.

And anyway, I want to install linux, not to reinstall windows.
What is the problem for linux to install itself to the already prepared partitions sda7, sda8, sda9, sda10.

Can you explain me this first, please.

Thank you.
I tried to explain that your HDD's partition table is unfortunately corrupt, and that's why the Ubuntu installer does not see your partitions. Even if you were able to install Ubuntu to your existing partitions, most likely you would have all kinds of problems with Grub, because Grub is extremely sensitive to partition table problems. I think it is inevitable that you will run into more problems until you correct your partition table, but it's up to you if you don't want to do anything. I think it's worth mentioning that I've helped quite a few people fix their partition tables in situations just like yours, so I'm only trying to help. If you would like an example, just a few days ago I helped someone with almost the exact same type of partition table problem as you:

[http://ubuntuforums.org/showthread.php?p=6620587](http://ubuntuforums.org/showthread.php?p=6620587)

Anyway, I will fully respect whatever you decide to do, because like I said, I'm only trying to help. :)

---

### Post by nimnull22 on 2009-01-28
To: Caljohnsmith

I really appreciate your help, thank you very much.

But I already have GRAB and it already booting me to win and to "some linux". And everything works good. Except for the fact that I want just to change "some linux" to ubuntu.
Win booting from sda5, and I don't know what GRAB will say if we change sda3 to logical partition. I need win for internet, because "some linux" can not go there.
The problem - is GRAB. I dont want it to says, that it can't find windows.

Thank you.

---

### Post by caljohnsmith on 2009-01-28
I don't know what else to say, because I think it is inevitable you will run into problems at some point because your partition table definitely needs fixing. I know you may still be skeptical whether your partition table really needs fixing, so how about doing:
```
sudo parted /dev/sda print
```
That command will normally show all the partitions on your sda drive, but if there is any problem with the partition table, it will return an error instead. If we do the steps I'm recommending to fix your partition table, it will take just a few extra steps to get Windows booting again after making it a logical partition, but I'm familiar with how to do that and have helped many others do it. I should mention I have to leave now and won't be around for another 10 hours or so until the morning, so we can pick up then if you want. It's entirely up to you.

---

