---
title: "New 500gß (SATA) Media Drive FAT32 issues"
date: 2009-10-23
forum: Hardware
---

### Post by jr226 on 2009-10-23
Hi, I just bought a 500 gß HDD (Seagate 7200 spin, SATA), with the goal of loading my media on it, to be read both by Win 7 and Kubuntu.  The drive would not format in Win 7, so I used Gparted in Kubuntu Live to try and format the drive.  Originially formatted to NTFS, but upon rebooting windows, it said the drive was write protected.  I then rebooted Kubuntu and formatted the drive to FAT32, thinking this would solve the problem.  Now the drive takes a while to find in the Windows Disk Manager (2 minutes), and will not show up in Gparted (either in Kubuntu or Gparted Live).

The drive will still not format in Windows, claiming an error that I can't recall right now, and is not recognized at all in Linux.  The Bios still shows that the HDD is detected.

Any advice on how I can format the drive?  Thanks!

---

### Post by jfernyhough on 2009-10-23
First, Giga-essen?

Second, are you sure it's plugged in correctly?

Otherwise it sounds like it would benefit from a new disk label (not a disk name) i.e. being initialised. Either use the Windows disk management tool to initialise, create a partition and format it as NTFS, or use GParted to create a new MSDOS disk label, create a partition and format.

I'd probably use the Windows tool so Windows can't complain.

---

### Post by jr226 on 2009-10-27
I checked, the drive is plugged in correctly, tried different SATA cables, and slots on my MB, including one that I know works, since I used it before and after for my DVD burner.

I have tried to re-initialize the disk, both using Windows and Kubuntu disks.  I got as far as being able to delete the FAT32 partition.  Now the disk shows up as a raw partition, drive letter F: in windows.

I tried to reinitialize the disk in Windows, and I get an I/O error message.  Trying to use parted (either live or in linux) results about 50% of the time with the F: drive being visable, and when it is, no luck on formatting.

I also tried formatting from the DOS prompt, and it stayed at 0% progress for about an hour before I gave up and Ctrl-c'd it out.  

The final thing I tried was downloading Seatool, Seagates diagnostic utility for their drives.  If I start the program and F: is displaying in both 'My Computer' and 'Disk Manager', it disappears while the 'Checking for Disks' window from SeaTool is displayed.

Any ideas?  RMA?

---

### Post by jfernyhough on 2009-10-30
The only other things I can think of before concluding it needs to be an RMA:

Is the drive getting enough power? How many devices do you have plugged in?
Have you tried it in another machine (or in an external enclosure)?
Is there a BIOS update for your machine?
Are you trying to run a SATA 3GBps drive off a SATA 1.5GBps port?

---

