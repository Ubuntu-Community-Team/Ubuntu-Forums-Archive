---
title: "Installation fails to boot and just resets"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by SteveLee on 2006-01-25
Hi, I'm having no luck getting a working system installed from the 5.10 CDs that I received from Ubuntu. The symptoms are that when the installer tries to reboot the machine after installing GRUB the machine continuously reboots. It restarts just after it fails to boot from CD so I guess is as it tries to get the MBR or run the boot loader.

I’ve done all I can to make the PC and Ubuntu config. as clean as possible by removing all cards except graphics / NIC / IDE Raid (all PCI) and just having the one CD and IDE Disk (120GB IBM). I told the Ubuntu partitioner to delete the partition table and picked erase and use all disk for / and swap. Partitioning and format all seem to work OK.

Any clues? Can we get any visibility of what’s happening?. Motherboard is only about 6 yrs old.

Cheers

Steve Lee
------------
schoolforge.org.uk – The Open Source community for education

---

### Post by Zimmer on 2006-01-25
[QUOTE=SteveLee]
 I told the Ubuntu partitioner to delete the partition table and picked erase and use all disk for / and swap. Partitioning and format all seem to work OK

[/QUOTE]
If you really told the partitioner to make one partition for root AND swap then that might be the clue...I'm no expert on partitioning (I've never found a simple to understand explanation of what is basically required...but...)
[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

[QUOTE=]
#

If you do not want to erase an entire disk, or if you want to customize the partition layout, choose "Manually edit partition table" from the menu, and the next screen will show you your partition table, how the partitions will be formatted, and where they will be mounted. Be aware that "Breezy Badger" requires about 1.8 Gb to install and operate, and any less than a 4 Gb root (/) partition with a 256 Mb swap partition can make the install process stop abruptly. We expect that this matter will be cleared up shortly.
#

Select a partition to modify or delete it. Remember to assign at least one partition for swap space and to mount a partition on /. Choose "Finish partitioning and write changes to disk" when you are finished.
[/QUOTE]
Maybe you have partitioned incorrectly,
or perhaps something simpler as discussed here
[http://ubuntuforums.org/showthread.php?t=99131&highlight=reboots](http://ubuntuforums.org/showthread.php?t=99131&highlight=reboots)

Specs of the machine here would help anyone else reading this to diagnose the fault..
Regards

---

### Post by SteveLee on 2006-01-26
Thanks Zimmer. Sorry I was not clear but I just used the default partitioning; one for / and one for swap.

I have now found that the problem is the PCI IDE controller card. Does Ubuntu not support them? Its a Hight Point HPT370/372

I use the controller card as I have a large fast disk and the onbard IDEs are slower that the disk can manage.

I proved this is the case as I put a slow old disk on the onbard IDE and installed OK. If I move the disk to the controller I get the reboots. I tried disabling the 2 onboard IDE channels in BIOS.

At least I have a usable system but really want to use my 120G disk at full spead.

Steve

---

### Post by SteveLee on 2006-01-26
Dam looks like I am out of luck

[http://www.ussg.iu.edu/hypermail/linux/kernel/0506.0/1305.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0506.0/1305.html)

Though my problem seems to happen earlier in the boot sequence.

Has anything been done since this old post?

---

### Post by Zimmer on 2006-01-29
Seems not,
I found this thread, unanswered. 
[http://ubuntuforums.org/showthread.php?t=64046&highlight=HPT372N](http://ubuntuforums.org/showthread.php?t=64046&highlight=HPT372N)
Might be an idea to ask the Dapper Developers...
Otherwise, sorry, I am unable to help..
Regards

---

### Post by nowotny on 2006-07-26
I just wanted to ask if this problem has been solved...? because I'm having the exact same issue on dapper...

---

