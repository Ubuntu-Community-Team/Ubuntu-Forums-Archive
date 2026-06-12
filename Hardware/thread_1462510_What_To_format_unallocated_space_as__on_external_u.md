---
title: "What To format unallocated space as  on external usb harddrive!!"
date: 2010-04-25
forum: Hardware
---

### Post by freesparks on 2010-04-25
Hello All,

  I have Ubuntu 9.10 installed on a 500GB Western Digital USB 2.0 harddrive and was wondering what to format the unused, unallocatedspace on it as.  I have over 234/5 GB of space left on it and want to use Ubuntu's Disk Utility to format it so i can use it for backup purposes to share files between MacOSX, Windows, and Ubuntu respectively.  Which is the best format that i can use in order to this?  Under Ubuntu's Disk Utility, it lists FAT, Linux Ext2, Linux Ext3, Linux Ext4, Linux XFS, NTFS, Swap Space, and Empty among the choices to be used.  All I was wondering is which is the best choice to use so that while either on Windows or Mac, or Linux, I can share files that I back up on this partition amongst all the major operating systems.  Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by Mewshi on 2010-04-25
I *know* FAT works under the big three; I'm pretty sure NTFS works under Mac OS X, but I'm not positive.

So, if you're willing to take a little risk (miniscule, at most) format the unused space as NTFS.  If you're not sure, format it as FAT.

---

### Post by conradin on 2010-04-25
Well what you dont want to format it as is swap space. 
probably the best choice is NTFS. FAT32 might also work for you. I would stay away from the others. HPFS, ext# wont work native with WIN OSes, OSX will probably work with anything you want to use (minus swap space) 
Im sure you can have 100 different opinions on this topic, there is lots of software out there to accommodate windows and EXT# file systems. 

I would stay away from fat16 too. There is a 4Gig limit on the partition size. See here:
[http://support.microsoft.com/kb/118335](http://support.microsoft.com/kb/118335)

---

### Post by freesparks on 2010-04-25
WOW,  Guys thank you and all the best.  Like I said on one of my other posts, this is one of the best tech supports that anyone can ask for.  I really appreciate the responses.  It looks like I'm going with NTFS then since I did read in one of the Linux books that I picked up that FAT format have limitations.

Best Regards,

freesparks

---

### Post by freesparks on 2010-04-25
Hello Guys,

  Using Ubuntu's Disk Utility, I tried to partition the unallocated free 255GB worth of space that I have and I got this error:

> Error creating file system: helper exited with exit code 1: cannot spawn 'mkntfs -f -L "LinuxBackup" /dev/sdb3': Failed to execute child process "mkntfs" (No such file or directory)

Any ideas in terms of what could be causing this???

Any help would be greatly appreciated!!

Best Regards,

freesparks

---

