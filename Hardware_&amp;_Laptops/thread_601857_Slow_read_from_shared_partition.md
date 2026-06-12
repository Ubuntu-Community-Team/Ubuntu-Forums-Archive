---
title: "Slow read from shared partition"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by immerohnegott on 2007-11-03
Just did a clean CD install of Gutsy (the net upgrade botched my setup, and i couldn't get my network to run). THAT problem was taken care of, but now I'm getting a slow read from my shared FAT32 partition -  this did not happen before the new install. When I try to open the partition, the window goes unresponsive for 5-10 seconds before the data loads and I'm able to browse the volume. 

My drives are setup as such (on intel ICH8 - four ports, two channels) - 
 
SATA1 Master - 250 WD2500KS SATA II : One partition, Windows XP bootable, NTFS.
SATA2 Master - 400 GB Seagate (forget the model #) SATA II :
            
             Partition 1 - FAT32 (storage. I used FAT so I could write to it from Linux)
             Partition 2 - Ubuntu install, ext3
             Partition 3 - Linux Swap

Not the end of the world, as I can still get data to/from the partition, it just worries me that there's something more sinister afoot with my filesystem/SATA.

---

### Post by Nzer24 on 2007-11-03
Well, number one, I don' think you needed to reinstall Gutsy. Often when the kernel or OS get a major upgrade, some drivers are removed. If you manually installed a driver, this is most likely the case. It happened to me with the Intel Gigabit Ethernet onboard ethernet card. 

Regardless, I have one theory about your problem. Maybe when you reinstalled, there were some files written to the FAT32 partition. As far as I know, Linux doesn't work it's non-fragmentation magic on non-ext or non-reiserfs systems, so maybe it's heavily fragmented. If you have a windows machine, you might be able to defragment it. If that's not the problem, I don't know what to do.

---

