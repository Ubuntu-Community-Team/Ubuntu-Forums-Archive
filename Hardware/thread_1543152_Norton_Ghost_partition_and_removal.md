---
title: "Norton Ghost partition and removal"
date: 2010-07-31
forum: Hardware
---

### Post by mtbinva on 2010-07-31
First, this is my first post here.  Lurked quite a bit and searched.  I have a great learning situation that I have hit a roadblock on.

I have a lab Win PC XP Pro SP3.  I have Norton Ghost 2003 loaded on it.  Purpose is to investigate a GHO (Noton Ghost file).  Ghost failed to mount so I ran the verify image utility.  It rebooted and got stuck in the reboot loop of not being able to boot back into windows.  I booted to an Ubuntu CD that also has some forensic software and can see the devices.

Question, how can I locate and delete the Ghost Virtual Disk as the primary boot device?  Please be patient, yes I know I'm a Newb, but tips and tricks would be welcomed.  My work flow wants to take me to mounting the NTFS volume of the drive and delete the actual Norton Virtual drive.  Buy that seems to almost self defeating in that the MBR would still need to be adjusted to remove the virtual boot device.

Does this make any sense or am I going about it the whole way? Again the purpose of this is to learn the Ubuntu/Unix platform much better.  I spent the day in virtual environment and learning many of the commands and switches and about mounting devices and the different methods to do that with an NTFS file system.

Thoughts? Tips? Direction?


Thank you in advance! and thanks for all of the posts I was and will be able to learn from.

---

### Post by oldfred on 2010-07-31
We really are a Ubuntu forum.:)

fixboot & fixmbr should get it back:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by mtbinva on 2010-07-31
Agreed, but it's with the Ubuntu boot I want to do this.

Thanks!:D

Thanks for the tutorial link, seems I was OVER complicating the whole process!

---

