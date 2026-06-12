---
title: "install xp or vista after Ubuntu 9.04"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by novio8 on 2009-06-02
Hi,
I have laptop with Ubuntu 9.04 installed.Disk has 3 partitions already. At work we use only windows software. I would like to install vista or xp without loosing ubuntu. I'm newbie so please be patient and simple as it gets

Mario

---

### Post by wyliecoyoteuk on 2009-06-02
Sorry, but not easy.
It would be easier to wipe the disk and install windows, then reinstall Ubuntu, as Ubuntu will resize the windows partition for you.

Otherwise, would need to resize your Ubuntu partitions to leave some free space for windows, install windows, then repair the boot loader so that you can dual boot.

---

### Post by novio8 on 2009-06-02
I already hava a partition free for xp or vista

---

### Post by kruegger on 2009-06-02
Then, install the Microsoft OS of your choice in that partition. By doing this, the GRUB boot-loader will be erased from the MBR, and Ubuntu won't boot.
Grub (grand unified boot-loader) is the program that allows for dual booting.
You have to install it again from your Ubuntu LiveCD. In order to do that, you have to know the partitions name in Unix systems. Instead of name it C: or H:, they are named hda1 or sda3, depending on the drive.

To know yours, boot from your LiveCD, open a terminal and type

sudo fdisk -l

and you'll see your hard drive's partition table.

To find out which partition is which, pay attention to the file system column: if it says ntfs or fat 32 it is a Windows partition. Otherwise should be a linux partition.
Once you know the partition name in which Ubuntu is installed, you know the parameters to reinstall GRUB.

The rest of it can be seen [HERE]("http://ubuntuforums.org/showthread.php?t=224351")

You should be fine with this introduction.

---

### Post by novio8 on 2009-06-02
Krueger thanx 
I'll try

---

