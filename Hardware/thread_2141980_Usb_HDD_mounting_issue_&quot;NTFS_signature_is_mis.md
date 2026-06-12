---
title: "Usb HDD mounting issue &quot;NTFS signature is missing&quot;"
date: 2013-05-04
forum: Hardware
---

### Post by RenegadeTigger on 2013-05-04
Ok so im new to Ubuntu, 
I feel I should state this first as it might explane the rest of the problem i have. My situation was a two part problem as follows: 

1st - when i installed Ubuntu i didnt backup all of my importaint files (a rookie error i know) so when i had i hunt around i discovered Testdisk and worked out i could recover my files i was happy. after getting myself a new HDD and an enclosure to house it i was set to back up some of the files.
2nd - the problem is it wouldnt read my new HDD... i search around and find i need to format it first, so i use Disk to format the HDD and we are all good, i trasfur some of the files and had to finish off later. i unmount the disk and when i next start up it wont read my HDD. fair enough i go back to reformat the HDD and start again, but now it comes up

"Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)"

at this point im not sure what to do.

The HDD is a 2tb sata seagate thats one day old. im running it off a system with only Ubutnu 13 on it. The laptop is a aspire 5742. 

when i ran "sudo fdisk -l" this is the result:

saint@saint-Aspire-5742:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004fe86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964863999   482430976   83  Linux
/dev/sda2       964866046   976771071     5952513    5  Extended
/dev/sda5       964866048   976771071     5952512   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000fc70

   Device Boot      Start         End      Blocks   Id  System

It dosent look as though its mounted, if i try to mount it is says:

"NTFS signature is missing"

so now im stumped, any guess's how i go about repairing the HDD?
any help here would be a great help!
Thanks

---

### Post by SeijiSensei on 2013-05-04
The drive isn't partitioned.  See how the main drive, /dev/sda, has three partitions, /dev/sda[123]?  The new drive has no partitions.  You'll need to create one yourself.

Try running "sudo gparted", then tell it to create a partition on the new drive.  If you intend to use the drive with Windows machines as well, make it an NTFS partition.  If you only intend to keep this drive attached to the Linux box, I'd create a Linux partition formatted with ext4.

If you don't have a copy of gparted, use "sudo apt-get install gparted" to get one.

If you are comfortable with the command line, you can do this with fdisk and mkfs, but gparted is probably easier.

---

### Post by RenegadeTigger on 2013-05-04
Thats ace thanks SeijiSensi, 
A quick and easy fix. works like a charm now! youve been a big help!!

---

