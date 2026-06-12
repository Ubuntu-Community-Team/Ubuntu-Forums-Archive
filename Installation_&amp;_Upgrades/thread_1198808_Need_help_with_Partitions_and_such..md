---
title: "Need help with Partitions and such."
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by romac1991 on 2009-06-27
Okay, so I'm a linux virgin and i was very excited to get my disk in the mail. I installed it, and I guess didn't really understand the bit about drive partitions, but it went ahead smoothly so I figured it was alright. But whenever I tried to download anything it told me I did not have any space on my disk. So I looked all over forums and places and I started trying to mess with the drive partitions on Vista. Vista had 280 GB of the Disk to itself, and it looked like Ubuntu barely had any. So I freed up space from Vista ( I think, I don't know what I'm doing) and I tried to get Ubuntu to work again. It didn't work, so for some reason I thought installing Ubuntu again would make it work, it didn't, so now I have two partitions ( I think ) for Ubuntu on my disk. I just want to get the partitions right so I have enough room to operate Ubuntu, and I want to delete the other Ubuntu I stupidly installed.

This is all very confusing to me, but I'm still excited about getting into Linux. 
I heard the Linux Community was supposed to be great at things like this, so I was hoping I'd find some friendly and helpful people to help me leave Vista behind.
Any help is greatly appreciated, thanks.

oh, and PS, if this has already been answered 100,000 times and its pissing you guys off, just yell at me where to find it. I've searched it quite a few times on here but didn't find exactly what I was looking for.

---

### Post by presence1960 on 2009-06-28
Don't feel bad there are many posts with the same problem. First lets get a look at what you have as far as partitions go. Open a terminal by going to Applications > Accessories > Terminal. paste this command in terminal or type it in ```
sudo fdisk -l
```BTW that is a lowercase L. Post the output back here and we'll see what you have.

---

### Post by romac1991 on 2009-06-28
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1531       38261   295041757+   7  HPFS/NTFS
/dev/sda3           38588       38913     2618595    5  Extended
/dev/sda5           38588       38891     2441848+  83  Linux
/dev/sda6           38892       38913      176683+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 16 MB, 16056320 bytes
2 heads, 32 sectors/track, 490 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         490       15651+   1  FAT12
brian@brian-laptop:~$

---

### Post by merlinus on 2009-06-28
You have two ubuntu partitions, and they are not duplicates.  sda5 is / (root) and sda6 is /swap.

But it may be useful to know the size of /, so run this command in a terminal and post results:

```

df -h

```

BTW, vista is on sda2.  sda1 is probably a recovery partition set up by your computer oem.

---

### Post by presence1960 on 2009-06-28
your linux partitions are way too small. you will definitely have to reinstall. let's start at the beginning:
1. Back up your data! Even though partitioning & installation process work almost flawlessly there is always the chance something can happen which results in data corruption/loss. Don't be the one crying you lost all your data.

2. Did you defrag windows at least once or twice prior to install? If not do so now.

3. I see you put Ubuntu in an extended partition. if this is what you want I would use Vista's disk management utility to delete those partitions & shrink the Vista partition. Then boot the Ubuntu Live CD or gparted Live CD to create an extended partition and the 2 logical partitions: 1 for Ubuntu & the other for swap. Swap I would recommend 1 to 1.5 times your RAM for swap partition size. For Ubuntu I would give at least 20 GB so you have room for software, updates and storage. The Ubuntu partition set as ext 3 or ext 4. The swap partition set as swap. I would read this also : [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

4. After you get your partitions in order you can install Ubuntu from the Ubuntu Live CD. When you get to the "Prepare disk space" window of the partitioner choose the manual option. See attached pic. Then highlight your intended Ubuntu partition. Set parameters such as Partition type to logical, Use as to ext 3 or ext 4 and mountpoint to /. Highlight intended swap partition and set parameters such as partition type to logical and Use as to swap. proceed with the install. 

5. When you get to the "Ready to install" window click the advanced button and choose hd0 or sda to install GRUB to MBR. see second attached pic. Proceed with the install and you should be good to go.

---

### Post by merlinus on 2009-06-28
Since you are reinstalling and theoretically will have lots more space, you may wish to consider creating a separate partition for /home, which is where application settings, configurations and such, as well as some data, are stored.

This will make reinstalling or installing a new version much easier.

Also, FWIW, cross and/or double posting about this issue only leads to confusion for those wishing to assist.

---

### Post by presence1960 on 2009-06-28
> **merlinus said:**
> Since you are reinstalling and theoretically will have lots more space, you may wish to consider creating a separate partition for /home, which is where application settings, configurations and such, as well as some data, are stored.

This will make reinstalling or installing a new version much easier.

Also, FWIW, cross and/or double posting about this issue only leads to confusion for those wishing to assist.

+1 

Just create another logical partition in the extended partition, set it as the same filesystem as ubuntu partition: ext 3 or ext 4.  when you are setting the parameters of the other partitions after choosing the manual option set your intended home as : Partitition type to logical, Use as to ext3 or ext 4 (same as Ubuntu or root / partition and mountpoint to /home.

P.S. please don't create multiple threads for the same topic. I guarantee you it will confuse you as well as us, then you won't get the most effective help.

---

