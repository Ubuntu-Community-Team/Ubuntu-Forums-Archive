---
title: "[SOLVED] Mounted Partition has Disappeared"
date: 2008-06-27
forum: Hardware
---

### Post by rldasilva on 2008-06-27
Hello, 
I am a complete newb to Linux (a friend converted me on Tuesday) and this is my first post on Ubuntu Forums.. I had my windows partition in /media/win/ and it worked perfectly for several days. However, last night I updated my linux and the Desktop icon for my mount disappeared. I then checked the Places scroll down menu and it was still there. Upon clicking on it I received the following message:

Cannot Mount Volume: You are not privilaged to mount this volume

Please help!

If you need any additional information (i.e. about my configuration) please describe how to get it so I can give it you. 

Thank you.

---

### Post by housam on 2008-06-27
Use this guide for [[COLOR="Red"]_mounting windows partitions_[/COLOR]]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by rldasilva on 2008-06-27
I looked through that site but unfortunately I did not set up the partition and I am unable to figure out how to fix the current issue I have.


I've found my fstab: here is it:
The drive in question is /dev/sda1 which had been mounted to /media/win


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b7752df4-684d-4089-9527-0737e416db56 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=5A20F05F20F04393 /media/win      ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=98595121-9586-4f8a-ba7a-5db5b6cec589 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by rldasilva on 2008-06-27
I have solved the problem.

The issue was that last time I shut down windows, it did not shut down properly. I rebooted, put it in windows and then shut it down (making sure it completed its cycle). Now my problem is Solved!

How do I flag this as SOLVED?

---

### Post by housam on 2008-06-27
> **rldasilva said:**
> I have solved the problem.

The issue was that last time I shut down windows, it did not shut down properly. I rebooted, put it in windows and then shut it down (making sure it completed its cycle). Now my problem is Solved!

How do I flag this as SOLVED?

Glad you solved it.
Go for page top >> thread tools >> mark thread solved

---

