---
title: "Reinstalling Windows on an Ubuntu system"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by timelord726 on 2006-02-09
As much as I loved living without Windows installed on my laptop, it's becoming more and more apparent that I need to have at least a small base install of Windows running on the side.  Is there any way that I can install Windows on my laptop without disrupting my existing Ubuntu system?  Even though I do need Windows, Ubuntu is still top priority and I don't want to mess things up.

Thanks in advance for any advice/assistance offered!  :)

EDIT: This might be of some assistance:
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4771    38323026   83  Linux
/dev/hda2            4772        4864      747022+   5  Extended
/dev/hda5            4772        4864      746991   82  Linux swap / Solaris
```

---

### Post by o_fortuna on 2006-02-09
[QUOTE=timelord726]As much as I loved living without Windows installed on my laptop, it's becoming more and more apparent that I need to have at least a small base install of Windows running on the side.  Is there any way that I can install Windows on my laptop without disrupting my existing Ubuntu system?  Even though I do need Windows, Ubuntu is still top priority and I don't want to mess things up.

Thanks in advance for any advice/assistance offered!  :)

EDIT: This might be of some assistance:
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4771    38323026   83  Linux
/dev/hda2            4772        4864      747022+   5  Extended
/dev/hda5            4772        4864      746991   82  Linux swap / Solaris
```[/QUOTE]
You can always reinstall windows; I don't *think* it will interfere, just make sure to be careful during the installation of windows. You might want to create the filesystem/leave open space using Ubuntu (Applications-->System Tools-->GParted) before beginning the installation. After you install, though, you'll have to restore GRUB on the MBR to boot Ubuntu. Information on how to do that can be found [here.]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29")

---

### Post by Bartender on 2006-02-09
I asked about this a month ago.  Don't remember the details but apparently it's easier to put Windows down 1st.

---

### Post by tim.w.ferguson on 2006-02-10
First, backup all data on hd.  Then repartition the drive so it has first partition for Windows and the rest for Linux (I would do 10G + 30G = 40G).  Install Windows on the first partition with FAT32.  Then install Linux on the rest of the drive.  Making the first partition FAT32 makes it easier to transfer/edit data back and forth between the two OS's.  Windows 98SE full install will actually fit in as small as about 350M so the rest of the space can be used for programs and data.  If you do the installs just right you sould be able to dual boot the machine.

tim....

---

### Post by Herman on 2006-02-10
> First, backup all data on hd. Then repartition the drive so it has first partition for Windows and the rest for Linux (I would do 10G + 30G = 40G). Install Windows on the first partition with FAT32. Then install Linux on the rest of the drive. Making the first partition FAT32 makes it easier to transfer/edit data back and forth between the two OS's. Windows 98SE full install will actually fit in as small as about 350M so the rest of the space can be used for programs and data. If you do the installs just right you sould be able to dual boot the machine. I agree with tim.w.ferguson, I have Windows 98 for one of my computers, and I can't get it to install to a partition, it insists on erasing the entire disk. Then for our WIndows XP computers here, our favourite brand of computer comes with 'Windows XP recovery CDs', as opposed to the regular 'Windows XP install CDs.' The recovery CDs also seem to erase the entire disk.

However, if you are lucky enough to have the 'install' type Windows XP disks, you might not need to erase Ubuntu, just resize it and install Windows XP on the free space you create and [re-install your GRUB bootloader]("http://www.ubuntuforums.org/showthread.php?t=24113") and you're laughing!
A good partitioning utility to use is [GParted livecd]("http://gparted.sourceforge.net/index.php"). That can shrink your Ubuntu partition to make the free space. A linux filesystem cannot be resized from the beginning though, only from the other end. If you want you can shrink it first, then copy it and paste it further down the disk, but I don't think you have to.  The beginning of the disk is the outside edge so it spins faster and some people say Windows is greedy for it, but  I think you can install Windows anywhere, I'm not 100% sure. GParted should be able to mkae your new fat32 partition for Windows too.
You'll need to edit /etc/fstab when you are through, too, probably.
Otherwise, just re-install, if that's what is easier and better for you. :-D (Herman).

---

### Post by lol on 2006-02-10
Parted cannot move the beginning of an ext3 filesystem, but you may want to try with other tools, otherwise it's going to be a pain to free some space at the beginning of your drive.
Try with the one provided on the Ultimate Boot CD : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
I never used it though, so I am not sure it will be able to do the job.

---

### Post by lol on 2006-02-10
Also, have you considered installing Windows on a virtual machine? This is definitively the best solution if you don't need windows for games. If you cannot afford VMWare, there are some free tools that can do the trick as well (I saw a lot of threads on the forum about this).

---

