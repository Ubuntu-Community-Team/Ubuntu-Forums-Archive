---
title: "MBR and Disk problems"
date: 2010-04-15
forum: Hardware
---

### Post by OliverG on 2010-04-15
Hi all,

I'm new to this forum so i apologise if my description is not specific enough.

A little background to the problem: I recently bought a new file server for my business (small company, no more than 10 employees). This time around i decided to go with a Linux solution over a windows one, as we have a lot of freelancers who use Mac's and now have Mac pros, which will connect to windows servers, but in general seem to be much slower etc.

The new server consists of a separate boot drive, and then 5 1tb SATA drives operating off a PCI-express LSI RAID card, which have been configured in RAID 5 through the Cards BIOS.

The drive appears fine in Ubuntu, but i seem unable to format it with a partition any larger than 1600gb, no matter the configuration. I'm aware that MBR has a limitation of 2tb, but i thought this was only applicable to a single physical disk.

I really don't want to format multiple partitions for logistical reasons, and the drive needs to be compatible with both Mac and PC.

Any insight into the problem would be much appreciated.

Kind Regards,

Oliver

---

### Post by srs5694 on 2010-04-15
With hardware RAID, the MBR's 2TiB limit applies to the combined RAID size. I'm not sure why you're having problems at 1600GiB (maybe a limitation of whatever you're using for partitioning), but you'll definitely need to ditch MBR to fix the problem.

In Linux, both libparted-based tools (such as the text-mode GNU Parted and the GUI GParted) and my own text-mode [GPT fdisk](http://www.rodsbooks.com/gdisk/) package can handle GUID Partition Table (GPT) disks. I wrote [an article for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) about the issues about a year ago, so read it for the details. As a "quickie," you should be able to get it working by selecting the "advanced" option and picking the GPT disklabel type in GParted or similar tools (see Figure 2 in my IBM developerWorks piece). I don't recall the precise details of the Ubuntu installer, but an option like this should be available somewhere along the line. Also, be sure to create a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) It's not mentioned in my developerWorks piece, but it can improve the reliability of the GRUB 2 boot loader used by Ubuntu 9.10.

One other comment: I *strongly* advise you to create multiple partitions. Dumping everything in a ~4TiB root (/) filesystem creates a very inflexible setup that's likely to cause problems down the road. At the very least, I recommend setting up a relatively small (5-20GiB) root (/) partition and putting everything else in /home (assuming that's where the bulk of the user files will go; split off another directory into its own partition if the bulk of that 4TiB is being used for something else). You might even want to set aside another ~5-20GiB partition for future installs. That way, you can install a new version of Linux in the future without disrupting your current install or your user data. If you have problems with the new version, you can revert back to the old one without trouble.

---

