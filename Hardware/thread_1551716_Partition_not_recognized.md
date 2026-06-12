---
title: "Partition not recognized"
date: 2010-08-12
forum: Hardware
---

### Post by zulubk on 2010-08-12
**Partition not recognized** 			
 			 			 		   		 		 		My desktop has dual operating system.

I had totally four partitions

1. 1st Windows XP partition
2. 2nd Windows XP partition
3. Linux partition
4. Linux swap partition

I wanted to delete the Linux partition but accidentally deleted both Linux partition and Linux swap partition. 

After that when I tried to restart my machine the system automatically got me into GRUB.

I tried to repair the windows XP OS using the windows XP cd. I tried the  repair option and it did not work. Instead of going through the normal  validation....it staright way took me to C:. I tried chkdsk with  possible options but it came back with one or more recoverable problems  error.
Then I tried DIR to list folders, it came back with directory enumeration issue.
I tried to create a folder, it gave me the access denied issue.

Desperately I did the mistake of issuing FIXBOOT and FIXMBR in the C drive.

Then rebooted and found that the GRUb was no longer getting loaded.

I then came to know about testdisk and tried the package Ubuntu 10.4  live cd and loaded tesdisk and followed the steps. I was partially  successfully in recreating the partition table. I was able to recover 1  windows partition, Linux partition and Linus Swap partition.  Unfortunately the system is recognizing one full partition as free  space.

I tried installing GRUB and now the machine is able to load GRUB on load
I recovered the data in the partition I recovered but still I am not  able to figure out a way to fix the other partition. Any help will be  really appreciated.

Thank you

---

### Post by efflandt on 2010-08-12
First of all it is not really clear what you intended to do.  You said you wanted remove the Linux partition and also accidentally removed swap.  But if you removed Linux, why do you need Linux swap?  And what tool or program did you use to remove the partitions, or did you remove the partition table?  Were you going to install a different Linux version on the previous Linux partition (in which case there was no need to remove the partition)? 

If you were booting from grub in the mbr, that would now work after removing Linux, because only the initial part of grub is in the mbr, the rest of it was on the deleted Linux partition.  So you needed to restore the Windows mbr (which fixmbr does) and mark the Windows boot partition as boot (which I imagine fixboot does, along with replacing any missing boot files) if you wanted to boot into Windows without Linux.  Why did you think that was a mistake?

It is also not clear what was, or is, on your two Windows partitions (what brand of PC?)?  Many have a first partition with some sort of restore or recovery to be able to restore your system, or images of original discs so you can create them if your system did not come with backup discs of the OS.  That might be FAT32 or possibly a hidden partition marked as a different type or unknown not mounted by Windows, so you do not accidentally mess it up.

You may get more useful answers if you tell us what was on the two Windows partitions (which was the system partition) and what are you trying to end up with?  It would have been a big help (and for future consideration) if you had saved the output of **sudo fdisk -l** before you started tampering with it.  I always do that now after 64-bit WinXP beta totally changed my hard drive geometry (cylinders and heads) and I caught a Linux version at that time before it was about to do the same thing.  It took guessing and trial and error with Linux fdisk to get the right geometry for that drive to be able to boot (no data lost) since I had only glanced at fdisk when shrinking my original XP Home partition.

---

### Post by zulubk on 2010-08-13
Hi...Thank you for the response.


The machine is a custom built one. 500 GB of WD hard disk

First I installed windows XP in partition 1 and it was the C drive. 
Then I created another windows partition, partition 2 for R drive
I installed linux which created a linux swap and linus partition.

Recently, I wanted to remove the whole of Linux and replace with Ubuntu....

So I opened the disk manager utility of windows and deleted the Linux and Linux Swap partition. When I tried to format, it gave me an error saying the format could not completed and I had to reboot.

When I restarted my machine....it took me to the GRUB

So impatiently I used the windows XP installation cd to recover windows.

The repair usually asks to enter the number 1 or 2 for loading the right operating system. But it directly started with "c:>". I could not see any folders.

I issued FIXBOOT, which gave a message saying that the boot record is missing and whether I would like to create one. I created one

I issued FIXMBR, which also gave a message saying that the MBR is missing and whether I would like to create one. I created one of this too.

I believe all of the above mentioned activities corrupted the partition table.

So I recovered the partition table using ubuntu live cd and testdisk package. This recovered all paritions except one, The C drive windows partition. This is getting displayed as a free partition.

I was then able to install grub back to the LINUX partition. I am not able to proceed further in recovering the missing partition. 

So I am missing the WINDOWS system partition. I was able to recover the other WINDOWS partition which had my data.

I will post the current picture and current fdisk details of my hard drive.

Please do let me know if this info is good enough.

---

