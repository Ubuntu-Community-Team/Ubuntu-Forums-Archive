---
title: "Permissions for Raid Array"
date: 2021-01-11
forum: Hardware
---

### Post by thebigman65 on 2021-01-11
Hello All,

So I am new to this forum and also new to the Linux platform.  I am in the process if building a NAS and I ran into an issue yesterday.  My steps so far have been:

- Installed ubuntu desktop 20.04.1 on my NAS. it is up and running and working fine.
- I have 4 WD Red Drives, 2 x 10TB and 2x6TB, I have created a RAID 5 Array using mdadm, and mounted the drive.
- inside the desktop GUI under disks and files (manager?), I can see the drive (18 TB array in disks) and the Storage (media/username) etc.

Problem:

- I cannot add folders or files to the drive as the permission are set for Root to be the only R/W access.
- I cannot change this in the GUI.
- I tried to run a command line sudo chmod a+rw, etc.  But that did not work.
- Now since I have run this command, when I click on the array on the side bar in the GUI, 2 windows pop up.....weird.

I apologise in advance if I am not posting thing I should be (i.e. relevant info) but this is the best way I know how to explain it ATM.

Thanks!

---

### Post by TheFu on 2021-01-11
You need to learn Unix permissions, assuming you have a native Linux file system, not NTFS or something else.
Unix is multi-user from the ground up, period.  Your files will likely need to be accessed by different users or by programs running under different userids.  Multi-user.
Any Unix permissions tutorial is fine. All Unixen work the same. Google "ubuntu permissions" to find the ubuntu one.

I'm loath to provide "an answer" because it would only solve 1 issue now then later today, you'll have 20 other issues due to that answer.  

Work through a tutorial, then spend 45 min playing around with 3 different userids, groups and every possible set of permissions until the answers are clear. do ths in  play directory somewhere under /tmp/
chown, chmod, touch, mkdir are the commands to use.

A tip:
Don't put files in the root of the mount point. Always create a subdir to place files and other directories. This will pay off if you need to move it elsewhere.
If this will hold media files, you'll probably want to make more subdirs for different types of media.  If multiple different users need their own file areas, make different directories for each.
Directories must have execute permissions for the userid to enter, based on the permissions model. The tutorial should cover that.

---

