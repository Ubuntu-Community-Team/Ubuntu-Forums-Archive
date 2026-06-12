---
title: "Reconfiguring Partition Table"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by acmariner99 on 2009-01-10
Hey all, I am trying to reconfigure my computer with ubuntu 8.1 and vista or xp depending on how to solve this. How do I COMBINE partitions. Windows' disk center will let me allocate space, but will not let me extend other partitions. I have Xubuntu 8.1 installed on the partition I want to extend. Can I combine partitions during Ubuntu setup? Can I extend the partition through Xubuntu? If I have to reconfigure my entire partition table, how do I preserve the "D" drive?

---

### Post by Herman on 2009-01-10
> Hey all, I am trying to reconfigure my computer with ubuntu 8.1 and vista or xp depending on how to solve this. 
How do I COMBINE partitions. 
Windows' disk center will let me allocate space, but will not let me extend other partitions. 
I have Xubuntu 8.1 installed on the partition I want to extend. 
Can I combine partitions during Ubuntu setup? 
Can I extend the partition through Xubuntu? 
If I have to reconfigure my entire partition table, how do I preserve the "D" drive?:confused: COMBINE partitions? 'D' drive? 'Extend' a partition? 'Windows Disc Center?' WTF? :confused:

Okay, let me see now....
According to the partition table rules, we can have one, two three or four 'primary' partitions, because there are four slots in the partition table in a dos type master boot record, (the first sector of every (formatted) hard disk, (if you're using Windows as your 'other' operating system you probably have a 'dos' type partition table).
If we want to make more than four partitions, we can, in that case we can have between zero and three 'primary' partitions, and one special one called an 'extended' partition. The 'extended' partition may contain between zero and sixteen 'logical partitions, linked to each other in a series.

There is a problem with 'COMBINING' partitions, (if I understand what it is you're talking about). You can delete a partition and resize another one to occupy the vacant space. However, when you delete the other partition you would lose any files in it of course, so you would want to have those backed up on some other media beforehand.
Partitions usually contain file systems, and the only way I know of to 'combine' two file systems is simply to copy all of the files from one file system and simply paste them into the other. Perhaps in the Windows world there's an app which does that and calls it 'combining' two partitions and keeps the actual procedure obscure or secret so as to keep users dependant on proprietary processes?  I'm not sure. 

You should stick to one partition editing program and not alternate between different hard disc partitioners.  Open Source partition table editors are well tested and a lot less buggy than proprietary 'disc managers'. The proprietary ones tend to corrupt people's partition tables far more frequently. Besides that, Windows only understands it's own file systems, the FAT series and NTFS, it has no idea about how to handle a Linux file system. 

Can you clarify which partition is 'D' partition? Is that partition number 1?,  or what partition are you talking about exactly?
Please post the output from 'sudo fdisk -lu', or a screencap from GParted, so someone can see what your present situation is in order to be able to help you,
```
sudo fdisk -lu
```Regards, Herman :)

---

### Post by cwsnyder on 2009-01-10
Two other quick questions prompted by your comments:  Did you re-partition and install Xubuntu on its own partition or did you install by WUBI or virtual machine?  Are you going into a GRUB menu or Windows Boot menu when you boot your machine?

If you are selecting your operating system by Windows Boot.ini boot menu, and especially if you installed a WUBI or virtual machine, that changes the answer to your question completely.

---

