---
title: "Ubuntu Installed. Dual Boot works. But Windows no longer recognizes drives."
date: 2008-09-03
forum: Hardware
---

### Post by OrangeKyo on 2008-09-03
I have an HP Pavilion Laptop with two internal hard drives of 160 gb each. I had Windows XP running on one hard drive and used the secondary hard drive for data. Recently I wanted to try ubuntu, so I backed up that data and installed Ubuntu on that secondary hard drive.  The installation is successful and I am reasonably pleased with it, and I am able to dual boot into Windows or Ubuntu using the Grub loader well enough.

However, although ubuntu is able to mount and read my windows disk, windows is no longer able to mount the ubuntu disk in my computer nor is it able to mount any external hard drive for that matter. I Somehow the installation of Linux/Ubuntu/Grub Loader is interfering with windows' ability to mount disks except for its own partition.

Now, under windowsXP device manager, it is able to verify the connection of both disks and even an external hard drive when it is plugged in, suggesting that windows is able to detect them somehow. But of course neither of the secondary drives display in My Computer.

When i type "cd F:\" in MS-DOS command prompt it states "The device is not ready"

Has anyone else had this problem? Can i get more information on the GRUB loader? Is there a way to remove it? Why can't I choose a boot disk using my natural system Bios?

Thanks for your help everyone, if I can get this fixed I think I will keep ubuntu. However I cannot afford to have windows windows be unable to file transfer between external drives.

- OrangeKyo

---

### Post by falcon61102 on 2008-09-03
Without the installation of seperate software, windows will not be able to read your Ubuntu install due to the file type.  While Ubuntu can read NTFS and ex3, Windows can't see ex3 by default.  As far as your external not working, that may be caused by it not being unmounted properly.

Unfortunately I forget the name of the software that will allow you to view ex3 partitions in Windows.  I look around and post back if I find it.

---

