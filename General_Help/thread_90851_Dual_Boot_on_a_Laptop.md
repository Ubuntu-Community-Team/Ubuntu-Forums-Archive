---
title: "Dual Boot on a Laptop"
date: 2005-11-15
forum: General Help
---

### Post by Mosey on 2005-11-15
Hi, 

I have a shared HP pavillion ze4900, and I want to install a dual boot system on it - booting winXP and ubuntu. 

How do I do this?

Thanks

---

### Post by 23meg on 2005-11-15
Is Windows already installed? If not, install Windows first, reserving space for Ubuntu and then install Ubuntu. If it is, just go ahead and install Ubuntu; it will automatically set up a boot menu where you can choose which OS to boot. If Windows takes up your whole disk, you'll need to shrink your Windows partition with a partitioning tool such as Gparted or Partition Magic to open up space for Ubuntu. In any case the safe method is the same: Windows first, and then Ubuntu.

---

### Post by trandojedi on 2005-11-15
yer... i do window then ubuntu.

i've never used a too such a partition magic; i usually just format, put windows on, put linux on.

if u wanna do what i do...
- insert the win cd and let it boot
- when it comes to the partition screen delete all partition (i think with d, then l for the first time then enter... or watever it says) then create your windows parition with 'c' then leave the rest as free space (u'll set ubuntu up on there)
- select the parition u created, not the free space
- install win there


- boot up ubuntu
- choose to manually edit the partition table
- select the free space (u should see free space and the partition for ur windows)
- choose to 'automatically partition free space'
- done
- done
- and ur done ;)

---

### Post by aruckert on 2005-11-16
Hi,

I should be easy. In fact, the Ubuntu installer should do most of the work for you if you already have WinXP installed :)

Even so, there are some things you should take into account:
- If possible, partition the disk before installing any operating system (OS). If it's not possible, BACK UP YOUR DATA and use a tool that would let you change the disk's partitions without erasing the installed OS. Something like Partition Magic. I know there are some open source tools but I can't remember the names of any of them :(

- I recommend to have one partition for Windows, two for Linux (OS and swap) and a separate one for your data. Do not use NTFS for your data partition because NTFS access from Linux is read only. Use FAT32 instead.

- Install Windows before installing Linux and do it in the first partition. I don't have much experience with WinXP but previous versions of Windows caused trouble if not installed in the first partition.

- Install Ubuntu in the second and third partitions. This is not necessarily so, but I will help to avoid problems if your disk is too big. So, your fourth partition will be your data partition.

You can find a complete instalation guide here:

[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/)

For your paticular question see: Booting other operating systems

As an example, I have a 80 GB hard drive with a Win2k/Ubuntu dual boot.
This is my partition table:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/hda2            1959        3786    14683410   83  Linux
/dev/hda3            3787        3917     1052257+  82  Linux swap / Solaris
/dev/hda4            3918        9729    46684890    f  W95 Ext'd (LBA)
/dev/hda5            3918        9729    46684858+   b  W95 FAT32

As you can see the first partition is Win2k (NTFS), the second and third are Ubuntu (operating system and wap) and the third one is data.

I hope this helped.
Have fun! :smile:

---

### Post by aysiu on 2005-11-16
[QUOTE=aruckert]Hi,

I should be easy. In fact, the Ubuntu installer should do most of the work for you if you already have WinXP installed :)[/quote] [This tutorial is great for that](http://users.bigpond.net.au/hermanzone/)

---

