---
title: "Ubuntu Only System"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by jedimasterk on 2009-05-23
Right now I am dual booting between Ubuntu 9.04 and Windows XP Pro. I have a 500GB SATA drive, and was wondering if I got rid of Windows XP, what would be the best way to partition my 500GB SATA drive for just Ubuntu 9.04. Basically a Linux only system. I am very rarely using XP anymore.

---

### Post by JC Cheloven on 2009-05-23
Well, it largely depends on your tastes and needs. 

I find useful to have a separate partition for my data, and moderate partition(s) for the operating system(s). Perhaps something like this:

- 25Gb ext4 partition for 9.04
- 400Gb ext3 partition for your data (ext3 is better tested)
- an extended partition to include the folowing:
-- 70Gb of free space, to try other distros, etc
-- swap partition (about the size of your ram)

Being inn an extended partition, you will not have limitations if in the mood of trying more than one extra distro.

Yust a possibility ...

---

### Post by jedimasterk on 2009-05-23
Right now I have the drive divided two ways. The first with XP (320GB) and the second with Ubuntu (160GB). How could I delete Windows and repartition the space. Also what needs to be done to Grub before deletion. I tried this before, and when I went to reboot, got a blinking cursor and had to reinstall Ubuntu.

---

### Post by Wa1k3rTXRang3r on 2009-05-23
1. boot into the Ubuntu Live Cd
2. go to System-->Administration-->Partition Editor
3. from there you can delete your windows partition and resize your other partitions to what you want them to be

as for grub ive never had a problem with it after deleting a windows partition

---

### Post by jedimasterk on 2009-05-23
Will it fix grub to reflect Windows XP no longer being there. I already have Ubuntu installed and don't want nothing to happen to it. I thought Grub was loaded into the MBR of the Windows partition.

---

### Post by ad_267 on 2009-05-23
If you do have problems with grub you don't have to reinstall Ubuntu. From the grub menu you can edit your /boot/grub/menu.lst file to correct it.

Edit: See here for how to set up grub if it's deleted: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jjbasken on 2009-05-23
If you edit your /boot/grub/menu.lst you can just comment out the Windows section at the bottom of the file and that will remove it from your grub menu.

---

### Post by jedimasterk on 2009-05-23
What would happen if I edited my /boot/grub/menu.lst and instead of just comment out the Windows section at the bottom of the file I deleted it from your grub menu. Then run the live disk and deleted the windows partition and created a new primary partition and called it backup. Would that work.

---

### Post by wannjanjic on 2009-05-23
> **jedimasterk said:**
> What would happen if I edited my /boot/grub/menu.lst and instead of just comment out the Windows section at the bottom of the file I deleted it from your grub menu. Then run the live disk and deleted the windows partition and created a new primary partition and called it backup. Would that work.
Yes, it will work.

---

### Post by jedimasterk on 2009-05-23
What part should I delete

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

