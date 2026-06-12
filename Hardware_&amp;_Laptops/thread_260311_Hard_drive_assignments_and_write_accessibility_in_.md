---
title: "Hard drive assignments and write accessibility in Kubuntu 6.06"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by jadamslsmo on 2006-09-18
Hi all. Please excuse this long post. I will describe a history of problems that I have had and found the solutions either in the forums or on my own. My current problem is related to these past problems, and I believe that knowledge of these prior items will help you diagnose the current problem, which is write accessibility of a hard drive connected through (but not using as) a RAID PCI card.

Hardware first:
Proc: AMD64 2800. MB has unused SATA connections (turned off in BIOS). 512M RAM, (2) HDDs connected to IDE0 on MB, (1) DVD burner connected to IDE1, NVIDIA graphics card, onboard NIC, PCI IDE RAID card w/ (1) drive on each connection (as a primary master and a secondary master, not RAIDed.)

First Problem (and my solution):
With all (4) drives connected, I tried loading Kubuntu 6.06 (32 bit) onto the third partition of the primary drive connected to IDE0 (on the MB). Windows XP Pro is loaded on partition 1 and partition 2 is swap. I wanted to manually partition my drives during the install and got really confused at the drive assignments (and missing drives.) HDE and HDF were the only two allowed and I could not manually configure either one. So my solution was this: while leaving the RAID card in the machine but disconnecting those two drives, I was able to load the OS where I wanted it (master hdd on IDE0, partition 3.) The hard drive assignments were odd, though. Windows is on /dev/hde1 and Kubuntu is on /dev/hde3. So this problem is solved by disconnecting the drives from the RAID card. Both OSes will boot. The primary slave drive on IDE0 (w/ (2) FAT32 partitions) is accessible to both OSes.

Second Problem (and Ubuntu Forums solution):
Weeks later, I connected the other two IDE drives to the RAID card as master drives (on primary and secondary inputs) and could not boot the Kubuntu OS. I could boot into Windows, though. I booted the machine from a Knoppix CD and edited the menu.lst file so that the “root=” did not point to the device assignment (/dev/hde3) but to the file system’s UUID (I’m not telling you about other unsuccessful attempts ](*,)  ), a solution I found on this board. Boot problem solved. Being new to Kubuntu, it took a while to figure out where to graphically edit mounting the hard drives (I’m used to Fedora and SuSE) and was surprised that Kubuntu didn’t automatically detect the drives and offer me some options such as where to mount…
One unfortunate side effect is that Kubuntu re-writes menu.lst to /dev/??? and I have to change it back whenever I update or change the kernel (I’m using the K7 kernel.) I should keep a text file in my grub directory with the UUID!

Third Problem (and as yet unsolved):
I decided to remove the secondary master drive from the RAID card. I remembered that I did have problems with mount points before, so I removed the entry for that drive in the GUI before I physically removed it. Now the drive connected to the primary RAID slot can only be accessed as READ ONLY (say through konqueror  or “kdesu kate”.) I CHMOD the directories to give all users all rights and that doesn’t work, either. The GUI setup indicates r/w and fstab indicates r/w. I edited fstab to point to the UUID instead of the dev label for both the root partition (/dev/hde3) and the drive on the RAID card (/dev/hdc1). As you know, FAT32 and NTFS don’t have UUIDs so I left those alone. I have write rights to my root partition, and the two FAT32 partitions. I still cannot write to this partition. I even can mount that RAID drive from Windows and write to it (I loaded an EXT3 driver for Windows.)
I am totally at wits end. I would like to be able to write to this drive. What do you think I should do?

---

### Post by jadamslsmo on 2006-09-24
I finally fixed my problem: FSTAB was marked to NOT CHECK the drive. It was marked 0 0 instead of 0 1. Apparently if the OS has an indication of a corrupt filesystem, it will mark it as read-only. I rebooted after the change and multiple errors were repaired on the drive. I can now write to the drive!

Joel

---

