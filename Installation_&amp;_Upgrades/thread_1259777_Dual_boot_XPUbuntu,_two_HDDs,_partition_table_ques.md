---
title: "Dual boot XP/Ubuntu, two HDDs, partition table question"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by Steve Francis on 2009-09-06
I have two bootable SATA hard disk drives in my desktop pc:
disk 1, already loaded with (and running) Windows XP
disk 2, with one empty FAT32 primary partition and one extended partition containing 3 logical NTFS drives that I store my data on.

My plan is to disconnect disk 1 and install Ubuntu 9.04 on the FAT32 primary partition of disk 2. I will then reconnect disk 1 and thereafter use the pc BIOS to determine whether to boot to XP or Ubuntu.

My question is:
If I install Ubuntu 9.04 on disk 2 as described above, will the XP installation on disk 1 still see the three logical drives on disk 2?

---

### Post by Bartender on 2009-09-06
Windows should still see the extended partition.

The part I'm wondering about is how the Ubuntu installer will react to your existing partitioning scheme.  The Ubuntu installer usually tries to set up an extended partition for swap.
I don't know if the installer would make swap a primary partition, or try to place swap inside the extended partition, or if you'd have to manually create your partitions and be sure to make swap primary.

---

### Post by presence1960 on 2009-09-06
Good question posed by Bartender. I would manually create the Ubuntu partitions with Gparted Live Cd and then perform a maunual install at the prepare disk space window of the installer. I hope you know Ubuntu won't work on a FAT or NTFS partition. You must choose a linux filesystem if you perform a manual install.

Instead of playing with BIOS to choose which OS to boot you can set disk 2 to boot first in the hard disk boot order in BIOS. Then we can help you add a windows entry to menu.lst so when GRUB boots you will have the option to boot into windows. Myself going into BIOS is too cumbersome when you can simply choose which OS to boot from GRUB. But it is your machine and you can do it that way if you prefer.

---

### Post by Steve Francis on 2009-09-07
Thanks for your replies.

(This is a late counter-reply from me because I have been backing up all my data files prior to installing Ubuntu.)

In a nutshell, Bartender was right - **Windows did still see the extended partition**.

This is what I did...

1. Used Partition Magic to format the primary partition on disk 2 as ext3 (as it turned out, this step was probably unnecessary but I wanted to be sure that the system was running Windows when the format was done).

2. Powered down and physically disconnected all drives except disk 2.

3. Inserted the Ubuntu installation disk, rebooted the pc and followed the on screen instructions.

4. At the 'partitioning' phase of the installation, I chose manual creation, deleted the existing ext3 partition and created three new ones:

(a) Primary 8575MB ext3 partition "/" at the beginning of the free space.
(b) Primary 8575MB swap partition at the end of the free space (note: pc has 4GB RAM).
(c) 10840MB ext3 partition "/home" in the remaining free space in between.*
* wasn't given a 'primary' or 'extended' choice for /home (don't know why)

5. Rebooted and checked that Ubuntu loaded properly (note: used space on "/" was 2.2GB). Installed proprietary nVidia driver.

6. Powered down and physically reconnected disk 1 (Windows XP).

7. Rebooted......Ubuntu loaded by default.

At this point I found out that I could not use my BIOS to specify the boot HDD! Oh no! :mad:

8. Luckily I found this thread: [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)  I followed the instructions and now use GRUB to select which operating system to boot into.

Have to say that the installation of Ubuntu was painless and I'm looking forward to trying out the applications.

I don't know if my partition choice in step 4 above was an optimum choice or even correct but it seems to work ok.

---

